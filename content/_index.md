---
# Leave the homepage title empty to use the site title
title: ""
date: 2022-10-24
type: landing

design:
  # Default section spacing
  spacing: "0.5rem"
  background:
        color: black

sections: 
  - block: resume-biography-3
    content:
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
      text: |
        <span style="color: black;">Philippe Bergna is an AI safety researcher with expertise in adversarial machine learning, red teaming, and robust AI evaluation. At Advai, he worked with the UK Ministry of Defence on 3D adversarial patches and successfully attacked the UK’s leading facial verification system using transferable adversarial examples. His research applies adversarial methods beyond attacks, leveraging them as tools for uncertainty estimation, active learning, and Out-of-Distribution (OOD) detection. Most recently, he has investigated data extraction risks in large language models and built a Retrieval-Augmented Generation (RAG) chatbot for AI safety research.</span>

    # Show a call-to-action button under your biography? (optional)
      button:
        text: Download CV
        url: uploads/resume.pdf
    design:
      # css_class: dark
      background:
        color: black
        image:
          # Add your image background to `assets/media/`.
          filename: stacked-peaks.svg
          filters:
            brightness: 1.0
          size: cover
          position: center
          parallax: false

  - block: collection
    id: papers
    content:
      title: Featured Publications
      filters:
        folders:
          - publication
        featured_only: true
    design:
      view: article-grid
      columns: 2


  # - block: collection
   #  id: news
   #  content:
   #    title: Recent News
   #    subtitle: ''
   #    text: ''
  #     # Page type to display. E.g. post, talk, publication...
  #     page_type: post
  #     # Choose how many pages you would like to display (0 = all pages)
  #     count: 5
  #     # Filter on criteria
  #     filters:
  #       author: ""
  #       category: ""
  #       tag: ""
  #       exclude_featured: false
  #       exclude_future: false
  #       exclude_past: false
  #       publication_type: ""
      # Choose how many pages you would like to offset by
  #     offset: 0
      # Page order: descending (desc) or ascending (asc) date.
  #     order: desc
  #   design:
      # Choose a layout view
  #     view: date-title-summary
  #     # Reduce spacing
  #     spacing:
  #       padding: [0, 0, 0, 0]

  - block: cta-card
    demo: true # Only display this section in the Hugo Blox Builder demo site
    content:
      title: Explore My Academic Journey
      text: |-
        Driven by curiosity and a desire to build reliable AI systems, I am committed to advancing the frontiers of machine learning through research in probabilistic models, uncertainty quantification, and interpretable AI.

        Connect with me through my publications, talks, or by reaching out directly!
      button:
        text: View Publications
        url: /publication/
    design:
      card:
        # Card background color (CSS class)
        css_class: "bg-primary-700"
        css_style: ""
---
