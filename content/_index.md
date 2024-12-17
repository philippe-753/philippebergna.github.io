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
        <span style="color: black;">Richard Bergna is a first-year PhD student in Advanced Machine Learning at the Cambridge Computentional and Biological Learning Group (CBL), under the supervision of Prof. Jose Miguel Hernandez-Lobato and Prof. Pietro Liò. His research focuses on uncertainty quantification in machine learning, with applications in decision-making under uncertainty, Gaussian processes, graph neural networks, and reinforcement learning. Previously, he completed his MPhil in Machine Learning and Machine Intelligence at Cambridge and graduated with first-class honors from the University of Bristol in Engineering Mathematics.</span>

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

  # - block: markdown
  #   content:
  #     title: '📚 My Research'
  #     subtitle: ''
  #     text: |-
  #       My research explores uncertainty quantification, graph neural networks, and probabilistic methods, with applications in decision-making systems and robust machine learning models. I aim to develop tools that enable more interpretable and trustworthy AI, especially in high-stakes areas like healthcare, finance, and autonomous systems.

  #      I am always interested in collaborating with those working on innovative approaches to machine learning and AI. Feel free to reach out if you share similar interests or have a project in mind!
  #   design:
  #     columns: '1'

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

  - block: collection
    content:
      title: Recent Publications
      text: ""
      filters:
        folders:
          - publication
        exclude_featured: true
    design:
      view: citation

  - block: collection
    id: talks
    content:
      title: Recent & Upcoming Talks
      filters:
        folders:
          - event
    design:
      view: article-grid
      columns: 1

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
