# Guide to Using Git and Git CLI while FRC Programming

Coming soon! In the meantime, see this doc: https://docs.google.com/document/d/1NePrEethFhoQQv6VUiASzOYpK84FSHwKw6qN7PlqUHg/edit

# To clone a repository
Often used to create code from a template
1. Go to the GitHub repo and select the "Clone" button.
2. Click the copy button to copy the link.
3. Open the terminal/command line from VSCode, or go to the folder and right-click, and then click "git bash here" in the menu.
4. Type ```git clone [url] <folder name>.``` (Brackets are mandatory, the other things are optional.)
5. Success! Start coding.

# To push code to GitHub.

1. Repeat step 3 above.
2. Type ```git add *``` or ```git commit -a``` if you deleted a file. If you type ```git commit -a```and a text editor pops up in your terminal, press ```i``` to type a commit message, and then press ```:wq``` to write. Skip step 4.
3. Type ```git status``` and make sure all changes are staged for commit.
4. Type ```git commit -m "[message]"```
5. Type ```git push origin master``` or ```git push origin main```, depending on the name of the main repo.
6. Success!