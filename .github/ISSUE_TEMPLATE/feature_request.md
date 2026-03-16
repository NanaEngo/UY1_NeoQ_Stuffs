---
name: ✨ Feature Request
description: Suggest new content, guides, or improvements
title: "[Feature]: "
labels: ["enhancement"]
assignees: []
body:
  - type: markdown
    attributes:
      value: |
        Thanks for suggesting a new feature or improvement!

  - type: textarea
    id: problem
    attributes:
      label: Problem Statement
      description: What problem would this solve?
      placeholder: "I'm always frustrated when..."
    validations:
      required: true

  - type: textarea
    id: solution
    attributes:
      label: Proposed Solution
      description: Describe what you'd like to see added
      placeholder: "I would like to see a guide about..."
    validations:
      required: true

  - type: dropdown
    id: category
    attributes:
      label: Content Category
      description: Which category does this belong to?
      options:
        - Python Programming
        - LaTeX/Scientific Writing
        - Research Methodology
        - AI Tools
        - Quantum Physics/Chemistry
        - General Development Tools
        - Other (please describe)
    validations:
      required: true

  - type: textarea
    id: other-category
    attributes:
      label: Other Category
      description: If you selected "Other", please specify
      placeholder: "Please describe the category"
    validations:
      required: false

  - type: textarea
    id: resources
    attributes:
      label: Additional Resources
      description: Any links, references, or examples that would help?
      placeholder: "https://..."
    validations:
      required: false

  - type: checkboxes
    id: contribution
    attributes:
      label: Would you like to contribute?
      description: Are you willing to help create this content?
      options:
        - label: Yes, I'd like to contribute this content
        - label: No, I'm just suggesting the topic

  - type: checkboxes
    id: terms
    attributes:
      label: Code of Conduct
      description: By submitting this request, you agree to follow our Code of Conduct
      options:
        - label: I agree to follow this project's Code of Conduct
          required: true
