name: Auto Comment
on: [issues]
jobs:
 
  webinar-comment:
    if: github.event.label.name == 'Webinar'
    runs-on: ubuntu-latest
    permissions:
      issues: write
    steps:
      - name: Add comment
        uses: peter-evans/create-or-update-comment@a35cf36e5301d70b76f316e867e7788a55a31dae
        with:
          issue-number: ${{ github.event.issue.number }}
          body: |
            ![](http://images.github.media/EloquaImages/clients/GitHubInc/%7B64693387-8abe-494c-8af0-7bde046a64d1%7D_hubot_512.png)
            
            👋 @${{ github.event.issue.user.login }}, thank you for opening this Master issue for your new Webinar.
            
            While I finish the labeling and assigment please go ahead and convert the `Tasks` in the **Task list for sub-issues** above ☝️ to an issue. 
            
            I will reach back to you in each Task issue where we will be working together on assets creation. See you!
  
  webinar-label:
    needs: webinar-comment
    runs-on: ubuntu-latest
    steps:
      - uses: Naturalclar/issue-action@v2.0.2
        with:
          title-or-body: "both"
          parameters: '[ {"keywords": ["I am based in AMER"], "labels": ["AMER", "grey", "MOPS"], "assignees": ["BrunoChester"]}, {"keywords": ["Webinar emails -"], "labels": ["grey", "Webinar-emails", "MOPS"], "assignees": [""]}, {"keywords": ["Task: Webinar landing pages -"], "labels": ["grey", "Webinar-pages", "MOPS"], "assignees": [""]}, {"keywords": ["Webinar lead upload -"], "labels": ["grey", "Webinar-lead-upload", "MOPS"], "assignees": [""]}, {"keywords": ["Task: Nurture emails -"], "labels": ["grey", "Nurture-emails", "MOPS"], "assignees": [""]}, {"keywords": ["I am based in EMEA", "Webinar emails - EMEA"], "labels": ["EMEA", "grey", "MOPS"], "assignees": ["jason-araujo"]}, {"keywords": ["I am based in APAC"], "labels": ["APAC", "grey", "MOPS"], "assignees": ["jason-araujo"]}, {"keywords": ["Description of Enhancement Request"], "labels": ["grey", "MOPS"], "assignees": ["mike421453"]}]'
          github-token: "${{ secrets.SECRET_NAME }}"
 
# All jobs below are for task issues created off of the Batch issue
 
  Webinar-email:
    if: github.event.label.name == 'Webinar-emails'
    runs-on: ubuntu-latest
    permissions:
      issues: write
    steps:
      - name: Add comment
        uses: peter-evans/create-or-update-comment@a35cf36e5301d70b76f316e867e7788a55a31dae
        with:
          issue-number: ${{ github.event.issue.number }}
          body: |
            ![](http://images.github.media/EloquaImages/clients/GitHubInc/%7B64693387-8abe-494c-8af0-7bde046a64d1%7D_hubot_512.png)
            
            Hi again @${{ github.event.issue.user.login }}! Let's get you focused on email creation! Please leave issue title, labeling, and assigment to me.
            
            - [Here](https://github.com/GitHub-MOPs/Test_repo/issues/165) is a collection of templates that might be helpful for you and speed-up your asset creation process.
            
            - Feeling ready? Please go ahead and type `/Email Builder` as a comment below to start :rocket:
            
            We totally get it if you want to use a Google Doc to create your email template. If that is the case just make a comment saying `MOPs Bot I want the Google Doc link` and I will link you to it right away.      
 
  Webinar-page:
   #  needs: test
    if: github.event.label.name == 'Webinar-pages'
    runs-on: ubuntu-latest
    permissions:
      issues: write
    steps:
      - name: Add comment
        uses: peter-evans/create-or-update-comment@a35cf36e5301d70b76f316e867e7788a55a31dae
        with:
          issue-number: ${{ github.event.issue.number }}
          body: |
            ![](http://images.github.media/EloquaImages/clients/GitHubInc/%7B64693387-8abe-494c-8af0-7bde046a64d1%7D_hubot_512.png)
            
            Hey there @${{ github.event.issue.user.login }}! Let's get you focused on landing page creation! Please leave issue title, labeling, and assigment to me.
            
            - [Here](https://github.com/GitHub-MOPs/Test_repo/issues/165) is a collection of templates that might be helpful for you and speed-up your asset creation process.
            
            - Feeling ready? Please go ahead and type `/Webinar landing page` or `/Webinar thank you page` as a comment below to start :rocket:
            
            We totally get it if you want to use a Google Doc to create your email template. If that is the case just make a comment saying `MOPs Bot I want the Google Doc link` and I will link you to it right away.
            
            # ![Recording 2022-01-20 at 02 59 23](https://user-images.githubusercontent.com/35078348/150297349-2584ede5-686e-409f-bf62-e74204db83a6.gif)
  
  
  Webinar-lead-upload:
    # needs: test
    if: github.event.label.name == 'Webinar-lead-upload'
    runs-on: ubuntu-latest
    permissions:
      issues: write
    steps:
      - name: Add comment
        uses: peter-evans/create-or-update-comment@a35cf36e5301d70b76f316e867e7788a55a31dae
        with:
          issue-number: ${{ github.event.issue.number }}
          body: |
            ![](http://images.github.media/EloquaImages/clients/GitHubInc/%7B64693387-8abe-494c-8af0-7bde046a64d1%7D_hubot_512.png)
            
            @${{ github.event.issue.user.login }}, please run `/Lead Upload` as a comment to share all that good stuff with us.
            
            ![Recording 2022-01-20 at 03 56 19](https://user-images.githubusercontent.com/35078348/150306319-82a4fe09-ab27-42b2-a41b-40705fb1440c.gif)
