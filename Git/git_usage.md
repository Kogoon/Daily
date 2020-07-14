git config --global user.name "name"     
git config --global user.email "git e-mail"   

git init   
git status   
git add . // all   
//git add "file name.extention"   

git commit -m "description" //snapshot   
//without commit nothing change. (can't use push)   

git remote add origin https://github.com/username/project_name.git // connect local to repository   

git remote -v //check   

git push origin master   
//if i have only master branch, i can use just "git push"(warn)   

// what is clone?   
same as "git clone"   
but, usually use client that have noting, pull server's project   

git clone "repository url"   

it will download repository's content, init automatically   

//how create "branch"   
git branch "branch name"   

without option, can see the list of branch   
git branch   
"branch name1"   
"branch name2"   
"*" master // "*" means current branch 
