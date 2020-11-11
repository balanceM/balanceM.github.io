---
id: 95
date: 2020-11-04T15:35:49+00:00
author: banana
layout: revision
guid: http://180.76.187.186/2020/11/04/94-revision-v1/
permalink: /2020/11/04/94-revision-v1/
---
# Homebrew 切换国内源

原文：<https://www.jianshu.com/p/a7b39f50d289>

## <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmirrors.ustc.edu.cn%2F" target="_blank" rel="noreferrer noopener"><code>中国科大</code></a>

__

<pre class="wp-block-code"><code># 修改 brew.git
> cd "$(brew --repo)" && git remote set-url origin https://mirrors.ustc.edu.cn/brew.git

# 修改 homebrew-core.git
> cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core" && git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git

# 修改 homebrew-bottles
> echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.bash_profile && source ~/.bash_profile

# 立刻生效
> brew update
</code></pre>

## <a href="https://links.jianshu.com/go?to=https%3A%2F%2Fmirrors.tuna.tsinghua.edu.cn%2F" target="_blank" rel="noreferrer noopener"><code>清华大学</code></a>

__

<pre class="wp-block-code"><code># 修改 brew.git
> cd "$(brew --repo)" && git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git

# 修改 homebrew-core.git
> cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core" && git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git

# 修改 homebrew-bottles
> echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles' >> ~/.bash_profile && source ~/.bash_profile

# 立刻生效
> brew update
</code></pre>

__

<pre class="wp-block-code"><code># 查看（诊断） brew 状态
> brew doctor

# 重置 brew.git
> cd "$(brew --repo)" && git fetch && git reset --hard origin/master

# 切回官方 brew.git
> cd "$(brew --repo)" && git remote set-url origin https://github.com/Homebrew/brew.git

# 重置 homebrew-core.git
> cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core" && git fetch && git reset --hard origin/master

# 切回官方 homebrew-core.git
> cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core" && git remote set-url origin https://github.com/Homebrew/homebrew-core.git

# 立刻生效
> brew update
</code></pre>

其他操作__

<pre class="wp-block-code"><code># 升级 brew
> brew upgrade

# 清理 brew
> brew cleanup</code></pre>