---
date: 2022-10-21
title: Interview Types
aliases: []
tags:
  - fridayTalk
  - interview
category: 
from: 
---
[[github_issue_clone_sprint_3|demo]]
- types of interview
	- OA(online assessment)
	- phone interview
	- onsite interview
- don't understand question
	- ask => may not get answers
- Interview Types
	- project
	- algo
		- how to make tree (like in terminal)
	- situation questions
	- brainteasers
# why we need tech interview?
- what interviewer expect?
	- tech
		- git(commit, pr ,branch ,rebase)
			- 情境題
		- new tech (is there any new tech in  project)
			- new but same kind of his used tech (how to arrange , how to learn it )
		- 框架
			- 概念題
				- 他解決了什麼？
				- 核心問題（hooks , 進階題底層概念 , 盡量開放式）
				- 是否讀懂問題
	- project
		- code
			- coding style
			- prettier
			- projects between projects(是否有進步)
	- personality
		- extrovert
		- responsibility
		- fast reaction
			- live coding
			- brainteaser
		- 如何教學（表達能力）
		- 技術熱忱（部落格，研討會）
		- 表達清楚（之後才能討論，提問題才聽得懂）
			- email 的往來細節
			- 面試是從收到信開始
# What interview expect
	1. logical thinking
	2. transform idea to code
	3. cs knowledge
	4. communication
		1. 有問題要問，問題及早曝光比有問題還好。
	5. face challenge
---

# What should we do ?
- 技術選型（詢問）
	- linter
	- style 
	- state management
- General
	- 時程
		- deadline
	- Tappay
- Layout
	- common（如何分section）
		- header
		- footer
		- 問ＲＷＤ
	- 是否需要做分頁？還是一頁
	- 是否有 UI library
- Function
	- React(原生或框架)
		- login 
			- oAuth
			- 內部
		- api文件
# What should we do ? 

```js
const nums = [1, 2, 4, 2, 3, 1, 5];

console.log(distinct(nums));


function distinct(nums){
	const result = [];

	for(let element of nums){
		const repeat = result.find(num => num === element)
		if(!repeat)result.push(element)
	}

	const sortedUniqArray = result.sort((a,b)=>a-b)
	
	return sortedUniqArray
}

```

## after question
- 複雜度
- 是否可以用js原生的 `array method`
---

### So?
	1. listen carefully & ask clarification
	2. sort or not sort ?
	3. example
	4. 空間複雜度
	5. brute force solution
	6. corner case
	7. **test**!
	8. speak your thought
	9. discuss
## More important
1. skill 
2. attitude
3. Don't quit
4. It's ok that you can't find the optimal solution
5. Growth mindset
6. there will be smthing you don't know
7. accumulate your knowledge 
8. focus on improvemment
## Resource
1. Cracking the Coding Interview
2. Codibility
3. leetcode
	1. 題目分類
	2. 30分鐘後就去看答案