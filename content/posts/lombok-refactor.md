---
title: "lombok结合Microsoft power automate重构VO"
date: 2023-11-16T09:12:30+08:00
draft: false
---

第一步： find . -name "*VO.java" | xargs grep "lombok"|awk -F":" '{print $1}' |sort | uniq >1
第二步：find . -name "*VO.java" |sort | uniq > 2
第三步：sort 2 1 1 | uniq -u