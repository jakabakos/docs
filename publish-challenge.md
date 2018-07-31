---
description: >-
  It's really great if you created a challenge that runs locally, but the best
  thing if you share it with others. To do this, you need to be an Avatao
  challenge creator. Let's see how.
---

# Publish your challenge on Avatao

At Avatao, we believe that there are many smart people around the world whose technical skills are invaluable, but they are also happy to share their experience with others. That's why we do our best to make the process of content creation and publication as easy as possible. At the same time, we exactly know that education must be fun and enjoyable. To achieve this, our contents have to meet high quality standards.

{% hint style="info" %}
Simply, each challenge or tutorial has to pass the automatic and manual review process, before being published. Please find below the details.
{% endhint %}

1. If we haven't contacted you before, please fill in this form.
2. Content creator should accept the invitation and link his _GitHub_ account with the platform.
3. After accepting the invitation, content creator should see a new menu item called “**Create challenge**” in the sidebar of his/her **Dashboard**. Please choose a license type \(normally, there is one option\) and insert a challenge repository name and a small description.  

   {% hint style="info" %}
   Please choose a _challenge repository name_ that describes what the problem is in the challenge, because this name cannot be changed later on. For example, **don’t call** your repository “_SQL injection_” because there can be a lot of such challenges.

   Try to be more specific such as "_SQL injection in Java via Hibernate_". Later, you will see that the name of the repository can be different from the name of the challenge, but we **strongly** **suggest** to have the same to be able to find it easier on Github. Example: if the name of your challenge is “_My Fantastic Challenge - 2018_” the name of the repository should be “my-fantastic-challenge-2018”.
  {% endhint %}

4. Once the content creator has a Github URL he/she should clone it via _HTTPS_ or _SSH_, if she/he had already uploaded her/his pubkey to Github.
5. Once the URL is cloned, a staging branch should be created as follows:

   ```bash
    git checkout -b staging
    git push -u origin staging
   ```

6. Since the **master** branch is **write-protected**, **only the staging branch can be used later on**. The main reason is that the English grammar is checked on this branch.
7. Use your preferred challenge template from our [challenge toolbox](https://github.com/avatao-content/challenge-toolbox) and copy all the necessary information \(excluding .git directory\) from there to the git repository you have just cloned.
8. Commit and push your changes and check whether a **pull request \(PR\)** can be opened to the **master** branch. Note that Github automatically performs certain tests to see if  all metadata is filled properly. Please always check the warnings on Github if something is not good. Important: Once the repository is created on Github, there are 4 weeks to complete this process, otherwise the challenge repository is automatically merged.  
9. When you are ready with a challenge, please open a PR \(pull request\). Github will automatically notify reviewers, when a corresponding PR is ready to be merged. Your team mentor \(responsible for guaranteeing the technical quality of your challenge\) and our internal reviewers \(e.g., English grammar, final quality check\) will then check your work. Without their approvals, the challenge will not be merged into the master branch. Note that your challenge build process can be checked at [challenge-builder.avatao.com](https://challenge-builder.avatao.com/).
10. If the challenge passes the reviews and its build is successful, creator should see the  challenge in the platform under his/her name, by choosing from the filter under the Challenges page in the platform.

