name: Auto Comment
on: [issues]
jobs:
 
  nurture-comment:
    if: github.event.label.name == 'Nurture'
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
            
            👋  @${{ github.event.issue.user.login }}! If you've given us the copy doc please disregard this message, otherwise, let's get you focused on asset creation!
            
            - [Here](#https://github.com/GitHub-MOPs/Test_repo/issues/165) is a collection of templates that might be helpful for you and speed-up your asset creation process.
            
            - Feeling ready? Please go ahead and type `/Email Builder` as a comment below to start :rocket:
            
           
  
  Nurture-label:
    needs: nurture-comment
    runs-on: ubuntu-latest
    steps:
      - uses: Naturalclar/issue-action@v2.0.2
        with:
          title-or-body: "both"
          parameters: '[ {"keywords": ["I am based in AMER"], "labels": ["AMER", "grey", "MOPS"], "assignees": ["BrunoChester"]}, {"keywords": ["Webinar emails -"], "labels": ["grey", "Webinar-emails", "MOPS"], "assignees": [""]}, {"keywords": ["Task: Webinar landing pages -"], "labels": ["grey", "Webinar-pages", "MOPS"], "assignees": [""]}, {"keywords": ["Webinar lead upload -"], "labels": ["grey", "Webinar-lead-upload", "MOPS"], "assignees": [""]}, {"keywords": ["Task: Nurture emails -"], "labels": ["grey", "Nurture-emails", "MOPS"], "assignees": [""]}, {"keywords": ["I am based in EMEA", "Webinar emails - EMEA"], "labels": ["EMEA", "grey", "MOPS"], "assignees": ["jason-araujo"]}, {"keywords": ["I am based in APAC"], "labels": ["APAC", "grey", "MOPS"], "assignees": ["jason-araujo"]}, {"keywords": ["Description of Enhancement Request"], "labels": ["grey", "MOPS"], "assignees": ["mike421453"]}]'
          github-token: "${{ secrets.SECRET_NAME }}"
