# Adding Questions

Questions should be written in the following format
```yaml
- # uuid Needs to be a random UUID - You can generate it from https://www.uuidgenerator.net/version4.  Use version 4
  uuid: 1b8fbe3c-aeb2-4b7d-a3ef-3082bf07efcc
  # Types can be MultipleChoice or SingleChoice
  type: MultipleChoice
  # Content should be in Markdown format
  content: What does SW DAO offer?
  hint: This is shown if user needs some help
  explanation: This is shown when the user answers the choice incorrectly
  answerKeys:
    - e0kl
  # should be from one of the predefined list of topics
  topic: "01_data_types"
  # should be from one of the predefined list of sub-topics, or can be a new one
  subTopics:
    - "string"
    - "variables"
  # Difficulty level should be one option from "Low" , "Medium", "High"
  difficultyLevel: "Low"
  choices:
    # Content should be in Markdown format
    - content: It offers crypto based mining applications for effective utilization
        of resources.
      # four character random string
      key: rtte
      # order in which the choice should appear
      order: 0
    - content: It offers strategic DeFi investment products which allocate capital
        based on Machine Learning
      key: e0kl
      order: 1
    - content: It offers coding and machine learning solutions to develop Defi
        applications.
      key: fklo
      order: 2
    - content: All of the about options
      key: pwlp
      order: 3
```
