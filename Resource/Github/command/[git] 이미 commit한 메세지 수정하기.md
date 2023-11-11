# [git] 이미 commit한 메세지 수정하기

![Alt text](img/image.png)

Git 사용 중 commit를 할 때는 꼭 메시지를 입력하게 된다. 때때로 오타를 입력하거나 commit한 후에 메시지를 수정하고 싶은 경우가 있을 때가 있다. 이러한 경우 세가지의 commit 메시지 수정 방법에 대해서 작성해보았다.

1. 마지막 commit 메시지 수정하기
2. 이전 commit 메시지 수정하기
3. 이미 push 한 commit 메시지 수정하기

## 1. 마지막 commit 메시지 수정하기

---

마지막에 입력한 commit 메시지를 수정하는데는 —amend 옵션을 사용합니다.

`**git commit --amend -m "commit_message”**`

또는 commit_message를 바로 입력하지 않고 vi에서 수정하는 방법이 있습니다.

`**git commit --amend**`

## 2. 이전 commit 메시지 수정하기

---

마지막 commit 메시지를 수정하는 방법을 알아보았는데요. 그렇다면 마지막 이전에 작성했던 commit 메시지를 수정하는 방법도 있겠죠?

마지막 commit 메시지를 수정하기 위해서는 `rebase` 명령을 사용합니다. 왜냐하면 실제로는 해당 commit으로 이동하고 commit 메시지를 수정하고 해당 branch에 다시 merge 하는 방식이기 때문입니다. `rebase`를 통해서 merge commit이 생성되는 것을 막고 깔끔하게 commit 메시지 자체만 남길 수 있습니다.(rebase는 다음 아티클에서 자세히 알아보겠습니다.)

`**git rebase -i HEAD~3**`

`rebase` 명령어와 `-i`를 함께 사용하면 rebase를 대화형으로 수행하여 여러 commit들의 순서를 바꾸거나 commit history를 변경 또는 삭제할 때 사용합니다.

`HEAD~3` 은 최근 commit log 중 3개를 불러온다는 의미입니다.

## 3. 이미 push한 commit 메시지 수정하기

---

이미 원격에 올라간 commit 메시지를 수정하는 방법은

`**git push--force <branch_name>**`

으로 원격에 덮어쓰는 방법이 있습니다.

이 방법은 권장되지 않으며 상황에 혼란을 야기 할 수 있습니다. **원격의 내용을 덮어쓰기 때문에 다른 팀원들이 이미 local에서 가지고 있는 commit log 메시지는 수동으로 수정해야하는 경우가 발생할 수 있습니다.**
