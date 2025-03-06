<template>
    <div class="guestbook-container">
      <h1>Guestbook</h1>
      <form @submit.prevent="submitComment" class="comment-form">
        <div class="form-group">
          <label for="name">Name</label>
          <input 
            type="text" 
            id="name" 
            v-model="newComment.name" 
            required
            placeholder="Your name"
          />
        </div>
        
        <div class="form-group">
          <label for="message">Message</label>
          <textarea 
            id="message" 
            v-model="newComment.message" 
            required
            rows="4"
            placeholder="Your message"
          ></textarea>
        </div>
        
        <button type="submit" :disabled="isSubmitting">
          {{ isSubmitting ? 'Submitting...' : 'Submit Comment' }}
        </button>
      </form>
      
      <div v-if="isLoading" class="loading">Loading comments...</div>
      
      <div v-else-if="error" class="error">{{ error }}</div>
      
      <div v-else-if="comments.length === 0" class="no-comments">
        No comments yet. Be the first to leave a message!
      </div>
      
      <div v-else class="comments-list">
        <h2>Comments</h2>
        <div v-for="comment in comments" :key="comment.id" class="comment">
          <div class="comment-header">
            <h3>{{ comment.name }}</h3>
            <span class="comment-date">{{ formatDate(comment.created_at) }}</span>
          </div>
          <p>{{ comment.message }}</p>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import { supabase } from '../supabase'
  
  export default {
    name: 'Guestbook',
    data() {
      return {
        comments: [],
        isLoading: true,
        isSubmitting: false,
        error: null,
        newComment: {
          name: '',
          message: ''
        }
      }
    },
    mounted() {
      this.fetchComments()
    },
    methods: {
      async fetchComments() {
        try {
          this.isLoading = true
          this.error = null
          
          const { data, error } = await supabase
            .from('comments')
            .select('*')
            .order('created_at', { ascending: false })
          
          if (error) throw error
          
          this.comments = data
        } catch (err) {
          console.error('Error fetching comments:', err)
          this.error = 'Failed to load comments. Please try again later.'
        } finally {
          this.isLoading = false
        }
      },
      async submitComment() {
        try {
          this.isSubmitting = true
          
          const { error } = await supabase
            .from('comments')
            .insert([
              {
                name: this.newComment.name,
                message: this.newComment.message
              }
            ])
          
          if (error) throw error
          
          this.newComment.name = ''
          this.newComment.message = ''
          
          await this.fetchComments()
        } catch (err) {
          console.error('Error submitting comment:', err)
          this.error = 'Failed to submit comment. Please try again later.'
        } finally {
          this.isSubmitting = false
        }
      },
      formatDate(dateString) {
        const date = new Date(dateString)
        return date.toLocaleDateString('en-US', {
          year: 'numeric',
          month: 'short',
          day: 'numeric'
        })
      }
    }
  }
  </script>
  
  <style scoped>
  .guestbook-container {
    max-width: 100%;
  }
  
  h1, h2 {
    margin-bottom: 1rem;
  }
  
  .comment-form {
    margin-bottom: 2rem;
  }
  
  .form-group {
    margin-bottom: 1rem;
  }
  
  label {
    display: block;
    margin-bottom: 0.5rem;
  }
  
  input, textarea {
    width: 100%;
    padding: 0.5rem;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  button {
    background-color: #333;
    color: white;
    border: none;
    padding: 0.5rem 1rem;
    border-radius: 4px;
    cursor: pointer;
  }
  
  button:disabled {
    background-color: #999;
  }
  
  .comment {
    border: 1px solid #eaeaea;
    padding: 1rem;
    margin-bottom: 1rem;
    border-radius: 4px;
  }
  
  .comment-header {
    display: flex;
    justify-content: space-between;
    margin-bottom: 0.5rem;
  }
  
  .comment-date {
    font-size: 0.8rem;
    color: #666;
  }
  </style>