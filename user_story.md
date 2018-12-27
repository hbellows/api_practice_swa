*Feature 1*

Uses: Sentences section on this page https://developer.oxforddictionaries.com/documentation

```As a guest user (no sign in required)
When I visit "/"
And I fill in a text box with "mindfulness"
And I click "Submit"
Then I should see a message that says "Examples for using 'mindfulness'"
And I should see a list of sentences with examples of how to use the word
And I should see only sentences where the region for usage is "British" or "Canadian"
And I should not see sentences for any other regions (or blank regions)```

*Feature 2: API - Viewing Game Score*

Background: This story assumes the base data from running `rake db:seed`

When I send a GET request to “/api/v1/games/1” I receive a JSON response as follows:

```{
  "game_id":1,
  "scores": [
    {
      "user_id":1,
      "score":15
    },
    {
      "user_id":2,
      "score":16
    }
  ]
}```

*Feature 3: API - Posting a Play*

Background: This story assumes the base data from running `rake db:seed`

You can choose to send the user_id and word specified below however you’d like or are comfortable.

When I send a POST request to “/api/v1/games/1/plays” with a user_id=1 and word=at
Then I should receive a 201 Created Response

When I send a GET request to “/api/v1/games/1” I receive a JSON response as follows:

```{
  "game_id":1,
  "scores": [
    {
      "user_id":1,
      "score":17
    },
    {
      "user_id":2,
      "score":16
    }
  ]
}```