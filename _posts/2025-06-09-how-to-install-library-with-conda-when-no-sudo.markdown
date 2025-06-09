---
layout:     post
title:      "how to install library with conda when no sudo and work on jupyter notebook"
date:       2025-06-09 12:00:00
author:     "yang"
header-img: "img/post-bg-miui6.jpg"
tags:
    - conda
    - library
    - sudo
---

> 这篇文章主要讨论没有权限，通过生成环境在如何添加到jupyter


<div>
    <blockquote>
    
      
# 1设置myparm环境ParmEd
conda create -n myparm python=3.10
# 2激活myparm环境
conda activate myparm
# 3在myparm环境中安装ipykernel为了可以在jupyternotebook中实现选中myparm环境
pip install ipykernel
# 或者
conda install ipykernel
# 3在myparm环境中安装ParmEd实现引用ParmEd
python setup.py install
    <br>
    
</div>
