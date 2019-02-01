branches=()
eval "$(git for-earch-ref --shell --format-'branches+=(%(refname))' refs/heads/)"
for branch in "${branches[@]}"; do
  if [[ "${branch}" != "master" ]]; then
git checkout ${branch}
git checkout master -- yourfile
fi

done
