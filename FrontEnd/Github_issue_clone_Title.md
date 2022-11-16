---
alias: 
tag: plan
---
[[github_issue_clone_sprint_4]]

# API

### Get an issue
`/repos/{owner}/{repo}/issues/{issue_number}`

### Patch an issue
`/{owner}/{repo}/issues/{issue_number}`

---
# Data needed
1. title
2. state
3. body
4. login(author)
5. number
6. comments
7. created_at
8. assignees(==only show on Mobile==)
9. labels(==only show on Mobile==)
---

```mermaid
graph TD

data--title-->demo前一個小時修改
	edit--clicked-->update
	edit--clicked-->cancel
	edit--clicked-->demo前一個小時修改---->Input

data--number-->#58
data--state--->open
data--state--->LinHeMa_opened_this_issue
data--login-->LinHeMa
data--creaded_at-->XXXago
data==comments==>Xcomments
```
