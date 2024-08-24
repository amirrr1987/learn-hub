<template>
  <section class="py-12">
    <div class="container mx-auto px-4">
      <h1>Contact Us</h1>
      <p>
        We would love to hear from you! Whether you have a question, feedback,
        or need support, our team is here to help. Please reach out to us
        through any of the methods below, and we will get back to you as soon as
        possible.
      </p>
    </div>
  </section>

  <section class="py-12">
    <div class="container mx-auto px-4">
      <h2>Contact Information</h2>
      <p>
        <strong>Email: </strong> 
        <a href="mailto:[Your Contact Email]">Maghami.A1987@gmail.com</a><br />
        <strong>Phone:</strong> [Your Contact Number]<br />
        <strong>Address:</strong> [Your Company Address]
      </p>
    </div>
  </section>

  <section class="py-12">
    <div class="container mx-auto px-4">
      <h2>Send Us a Message</h2>
      <form @submit.prevent="submitForm">
        <div class="form-group">
          <label for="name">Name</label>
          <input type="text" id="name" required />
        </div>
        <div class="form-group">
          <label for="email">Email</label>
          <input type="email" id="email" required />
        </div>
        <div class="form-group">
          <label for="subject">Subject</label>
          <input type="text" id="subject" required />
        </div>
        <div class="form-group">
          <label for="message">Message</label>
          <textarea id="message" rows="5" required></textarea>
        </div>
        <button type="submit">Send Message</button>
      </form>
    </div>
  </section>

  <section class="py-12">
    <div class="container mx-auto px-4">
      <h2>Our Location</h2>
      <!-- Embed a Google Map or any other map service -->
      <iframe
        src="https://www.google.com/maps/embed?pb=[Your Google Maps Embed Code]"
        width="100%"
        height="400"
        frameborder="0"
        style="border: 0"
        allowfullscreen=""
        aria-hidden="false"
        tabindex="0"
      >
      </iframe>
    </div>
  </section>
</template>
