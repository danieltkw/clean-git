



for repo in $(ls -d */); do
  repo=${repo%/}  # Remove trailing slash
  echo -e "\n🔍 Checking repository: $repo"
  cd "$repo" || continue

  if [ -d ".git" ]; then
    echo "✅ Git is initialized in $repo."
    commit_count=$(git rev-list --count HEAD 2>/dev/null)

    if [ "$commit_count" -eq 1 ]; then
      echo "✅ $repo is already clean with only 1 commit."
    else
      echo "⚠️ $repo has $commit_count commits. Cleaning history..."
      rm -rf .git
      git init
      git add .
      git commit -m "Clean history: keeping only latest commit"
      git branch -M main
      git remote add origin "https://github.com/danieltkw/$repo.git"
      git push --force origin main && echo "✅ Successfully reset history for $repo." || echo "❌ Failed to push $repo."
    fi
  else
    echo "⚠️ Git is NOT initialized in $repo. Reinitializing..."
    git init
    git add .
    git commit -m "Clean history: keeping only latest commit"
    git branch -M main
    git remote add origin "https://github.com/danieltkw/$repo.git"
    git push --force origin main && echo "✅ Successfully reinitialized and pushed $repo." || echo "❌ Failed to push $repo."
  fi
  
  cd ..
done



for repo in $(ls -d */); do
  repo=${repo%/}
  if [ -d "$repo/.git" ]; then
    echo "🔍 $repo:"
    cd "$repo" || continue
    git log --oneline | wc -l
    cd ..
  fi
done

