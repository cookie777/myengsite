---
# title: "{{ replace .Name "-" " " | title }}"
# title: "Dairy ;  {{ dateFormat "1/2/2006" .Date }}"
title: "Diary {{ dateFormat "1/2/2006" .Date}}"  
date: {{.Date }}
draft: false
---

