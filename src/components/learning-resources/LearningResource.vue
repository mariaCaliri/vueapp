<template>

  <li>
    <base-card>
      <div>
        <header>
          <h3>{{ name }}</h3>
          <base-button mode="flat">Delete</base-button>
        </header>
        <p>{{ description }}</p>
        <nav>
          <a :href="link">View the resource</a>
        </nav>
      </div>
    </base-card>
  </li>
</template>

<script scoped>
export default {
    props: {
        name: {
            type: String,
            required: true
        },
        description: {
            type: String,
            required: true
        },
        link: {
            type: String,
            required: true
        }
    },
    data() {
        return {
             
            
        }
    },
    methods: {
        
    },

}


</script>

<style> li {
    margin: auto;
    max-width: 40rem;
  }
  
  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  h3 {
    font-size: 1.25rem;
    margin: 0.5rem 0;
  }
  
  p {
    margin: 0.5rem 0;
  }
  
  a {
    text-decoration: none;
    color: #ce5c00;
  }
  
  a:hover,
  a:active {
    color: #c89300;
  }</style>