---
name: 🐛 Bug Report
description: Report a broken link, error in content, or technical issue
title: "[Bug]: "
labels: ["bug"]
assignees: []
body:
  - type: markdown
    attributes:
      value: |
        Thanks for taking the time to fill out this bug report!

  - type: input
    id: file
    attributes:
      label: Affected File
      description: Which file(s) are affected?
      placeholder: "e.g., Python_Tricks/UY1_NeoQ_Git_GitHub250730.md"
    validations:
      required: true

  - type: textarea
    id: description
    attributes:
      label: Bug Description
      description: Clearly describe the issue
      placeholder: "The link to X is broken..."
    validations:
      required: true

  - type: textarea
    id: expected
    attributes:
      label: Expected Behavior
      description: What should happen?
      placeholder: "The link should point to..."
    validations:
      required: true

  - type: textarea
    id: screenshots
    attributes:
      label: Screenshots (if applicable)
      description: Add screenshots to help explain the problem
      placeholder: "Drag and drop images here"
    validations:
      required: false

  - type: dropdown
    id: severity
    attributes:
      label: Severity
      description: How severe is this issue?
      options:
        - Low (typo, minor formatting)
        - Medium (broken link, confusing content)
        - High (major error, misleading information)
    validations:
      required: true

  - type: checkboxes
    id: terms
    attributes:
      label: Code of Conduct
      description: By submitting this issue, you agree to follow our Code of Conduct
      options:
        - label: I agree to follow this project's Code of Conduct
          required: true
