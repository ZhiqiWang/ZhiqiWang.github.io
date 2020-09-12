# Automotive Depoly Blog with Hugo


Just a memo. 

<!-- more -->

1. Add `publishDir = "zhiqiwang.github.io"` in config.toml. 
2. Create a `deploy.ps1` as below. 

```powershell
copy-item -path 'D:\Google Cloud\github\BlogSource-Zhiqi\posts\*.*' -Destination 'D:\Google Cloud\github\zhiqiblog\content\post\' -Force
d:
#cd 'D:\Google Cloud\github\zhiqiblog\themes\even'
#git pull
cd 'D:\Google Cloud\github\zhiqiblog\'
Remove-Item -Path zhiqiwang.github.io -Recurse -Force
hugo -D
copy-item -path 'D:\Google Cloud\github\zhiqiwang.github.io\.git' -destination 'D:\Google Cloud\github\' -Recurse -Force
remove-item -path 'D:\Google Cloud\github\zhiqiwang.github.io' -Recurse -Force
mkdir 'D:\Google Cloud\github\zhiqiwang.github.io'
copy-item -path 'D:\Google Cloud\github\.git' -destination 'D:\Google Cloud\github\zhiqiwang.github.io\' -Recurse -Force
remove-item -path 'D:\Google Cloud\github\.git' -Recurse -Force
Copy-Item -path zhiqiwang.github.io -destination 'D:\Google Cloud\github\' -Recurse -Force
cd ..\zhiqiwang.github.io\
git add .
git commit -m "update $(date)"
git push
cd 'D:\Google Cloud\github\BlogSource-Zhiqi'
```
