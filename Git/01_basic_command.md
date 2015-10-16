## Git Command

## commit
  * 현재 내 로컬 저장소에 데이터를 Stage Area에 올린다.
  * -m 명령으로 코멘트 가능
```
  git commit file.txt -m "modify file change" // 코멘트 커밋
```

## add
  * 현재 추가 되지 않은 파일들을 스테이지에 추가한다.
```
  git add file.txt  	// file.txt 추가
  git add .		// 현재 폴더에서 추가되지 않은 파일 모두 추가.
```

### Staging Area 생략하기
  * Staging Area는 커밋할 파일을 정리한다는 점에서 매우 유용하지만 복잡하기만 하고 필요하지 않은 때도 있다. 아주 쉽게 Staging Area를 생략할 수 있다. 
  * git commit 명령을 실행할 때 -a 옵션을 추가하면 Git은 Tracked 상태의 파일을 자동으로 Staging Area에 넣는다. 그래서 git add 명령을 실행하는 수고를 덜 수 있다:

```
  git commit file.txt -a 				// 추가와 커밋 동시에.
  git commit file.txt -am "add and commit comment"	// 추가와 커밋 동시 + 코멘트
 
```

## status
  * 현재 스테이지의 상태를 표시한다.

```
// git add file.txt를 이용하여 스테이지 파일이 추가 된 경우
> git status
On branch s up-to-date with 'origin/master'.

Change to be committed:
 (use "git reset HEAD <file>..." to unstage)
	new file: file.txt
```



