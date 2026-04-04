### Task-1

1. Branch is like a seperate workspace where you can make changes and implement new features without affecting code present in main project/branch
2. Whenever you implement a new feature or starting to implement new feature never commit directly in main branch , create another branch test the code completely and then merge feature into main branch
3. HEAD is nothing but a pointer to the latest commit in current branch , it basically keep track of yourlatest commit.
4. When you switch branches, Git updates your working directory to match the snapshot of that branch. Files may change, appear, or disappear depending on the branch content.

### Task-2

1. git branch
2. git branch feature-1
3. git checkout feature-1
4. git checkout -b feature-2
5. git switch feature-1
6. git add git-commands.md
   git commit -m "Added more commands in feature-1 branch"
7. git switch master
8. git branch -d feature-2

### Task-3

2. git remote set-url origin git@github.com:Dishank-05/Handson_Repo.git
3. git push origin master
4. git push origin feature-1
6. Origin means your personal repository on remote server where you can push your changes whereas upstream refers to original or central repository from where you have forked the code.

### Task-4

2. git pull origin feature-1
3. git fetch will fetches latest changes,files and branches from remote repo to your machine but it doesnt merge with your working directory whereas git pull is combo of git fetch + git merge it downloads changes and merge it with your current branch

### Task-5

1. git clone https://github.com/octocat/Hello-World.git
2. git clone https://github.com/Dishank-05/Hello-World.git
3. Fork means you are creating a copy of someone else repo under your Github Account which allows you to make changes without affecting original repository whereas cloning a git repository is like you are downloading a repository to your local machine . You should only use fork when you want to contribute in open source and use clone when you are working on your own repository where you have write access.

To keep your fork in sync

1. Add upstream remote:
   git remote add upstream <original-repo-url>

2. Fetch latest changes:
   git fetch upstream

3. Merge changes into your branch:
   git checkout main
   git merge upstream/main

4. Push updated code to your fork:
   git push origin main
    
