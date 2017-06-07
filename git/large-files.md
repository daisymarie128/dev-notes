## Using large files with gut

### git lfs
[git lfs](https://git-lfs.github.com/) is an open source extension for versioning large files.<br>
LFS stands for Git Large File Storage. This replaces large files such as audio samples,videos, datasets and graphics with text pointers inside Git. While it also stores the file contents on a remote server like github.com.

##### To install
Using Hombrew: `brew install git-lfs`

now inside your repo run:<br>
`git lfs install`
<br>
Then you can either specifically type what you want to manage. i.e<br>
`git lfs track .psd`
<br>
OR
<br>
Make sure .gitattributes is tracked. Example file:<br>
```
*.png filter=lfs diff=lfs merge=lfs -text
*.psd filter=lfs diff=lfs merge=lfs -text
```
<br>
Then just commit and push to github like normal<br>
```
git add example.psd
git commit -m "Add large file"
git push origin master
```