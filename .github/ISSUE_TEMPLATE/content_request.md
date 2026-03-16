---
name: 📝 Content Request
description: Request new tutorials, guides, or documentation
title: "[Content]: "
labels: ["documentation"]
assignees: []
body:
  - type: markdown
    attributes:
      value: |
        Suggest new content or documentation for the repository!

  - type: input
    id: topic
    attributes:
      label: Topic
      description: What topic should be covered?
      placeholder: "e.g., Introduction to Quantum Computing"
    validations:
      required: true

  - type: dropdown
    id: format
    attributes:
      label: Preferred Format
      description: What format would you prefer?
      options:
        - Markdown Guide (.md)
        - Jupyter Notebook (.ipynb)
        - PDF Document
        - Code Examples
        - Video Tutorial Link
        - Other
    validations:
      required: true

  - type: textarea
    id: description
    attributes:
      label: Description
      description: What should this content cover?
      placeholder: "This guide should explain..."
    validations:
      required: true

  - type: textarea
    id: audience
    attributes:
      label: Target Audience
      description: Who is this content for?
      placeholder: "Beginners in quantum physics..."
    validations:
      required: true

  - type: textarea
    id: prerequisites
    attributes:
      label: Prerequisites
      description: What knowledge is needed before reading?
      placeholder: "Basic Python knowledge..."
    validations:
      required: false

  - type: textarea
    id: references
    attributes:
      label: References
      description: Any existing resources that could help?
      placeholder: "Links to similar guides, documentation, etc."
    validations:
      required: false

  - type: checkboxes
    id: terms
    attributes:
      label: Code of Conduct
      description: By submitting this request, you agree to follow our Code of Conduct
      options:
        - label: I agree to follow this project's Code of Conduct
          required: true
