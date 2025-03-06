<template>
    <div class="container">
      <div class="card">
        <h1 class="text-center mb-3">Guestbook</h1>
        <p class="text-center mb-4">
          Leave a message in my guestbook! I'd love to hear from you.
        </p>
        
        <form @submit.prevent="submitComment" class="mb-4">
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
          
          <button 
            type="submit" 
            :disabled="isSubmitting"
          >
            {{ isSubmitting ? 'Submitting...' : 'Submit Comment' }}
          </button>
        </form>
        
        <div v-if="isLoading" class="text-center mb-4">
          <div class="spinner"></div>
          <p>Loading comments...</p>
        </div>
        
        <div v-else-if="error" class="text-center mb-4" style="color: red;">
          {{ error }}
        </div>
        
        <div v-else-if="comments.length === 0" class="text-center mb-4">
          No comments yet. Be the first to leave a message!
        </div>
        
        <div v-else>
          <h2 class="mb-3">Comments</h2>
          <div v-for="comment in comments" :key="comment.id" class="comment">
            <div class="comment-header">
              <h3>{{ comment.name }}</h3>
              <span class="comment-date">{{ formatDate(comment.created_at) }}</span>
            </div>
            <p>{{ comment.message }}</p>
          </div>
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
          
          // Reset form
          this.newComment.name = ''
          this.newComment.message = ''
          
          // Refresh comments
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