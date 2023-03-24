---
title: Cloud Manager 저장소
description: Cloud Manager 프로그램의 저장소에 액세스, 생성 및 편집하는 방법에 대해 알아보십시오.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 63cbcf8724a840efa67b8fafc4c321e04a5d70d9
workflow-type: ht
source-wordcount: '796'
ht-degree: 100%

---


# Cloud Manager 저장소 {#cloud-manager-repos}

저장소는 git을 사용하여 코드를 관리하는 곳입니다. Cloud Manager 프로그램의 저장소를 생성하는 방법에 대해 알아보십시오.

## 저장소 액세스 {#accessing-repos}

Cloud Manager에서 셀프서비스로 git 저장소에 액세스하고 관리할 수 있습니다.

저장소에 액세스하려면 Cloud Manager(주로 파이프라인 카드)에서 제공되는 **저장소 정보 액세스** 버튼을 사용하십시오.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동한 다음 **저장소 정보 액세스** 옵션을 찾아 [이 파이프라인으로 구성된](/help/using/production-pipelines.md) git 저장소에 액세스하고 관리합니다.

   ![저장소 정보 액세스 버튼](/help/assets/access-repo1.png)

1. **비프로덕션** 파이프라인 탭으로 전환하면 [파이프라인에 구성된](/help/using/non-production-pipelines.md) 대로 **저장소 정보 액세스** 옵션도 사용할 수 있습니다.

   ![비프로덕션 파이프라인 ](/help/assets/access-repo-nonprod.png)

1. **저장소 정보 액세스** 버튼을 클릭하여 다음 정보가 표시되는 대화 상자를 엽니다.

   * git 저장소의 URL
   * 사용자 이름
   * 암호
   * 로컬로 저장소를 복제하기 위해 실행할 git 명령

   ![저장소 정보 대화 상자](/help/assets/access-repo-create.png)

제공된 정보를 사용하여 로컬 개발을 시작할 수 있도록 저장소를 로컬로 복제합니다.

>[!NOTE]
>
>**저장소 정보 액세스** 옵션은 **개발자** 또는 **배포 관리자** 역할이 있는 사용자에게 표시됩니다.

## 저장소 추가 {#add-repos}

다음 단계에 따라 Cloud Manager에서 저장소를 추가하십시오.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **저장소** 탭을 클릭하고 **저장소** 페이지로 이동합니다.

1. **저장소 추가**&#x200B;를 클릭하여 마법사를 시작합니다.

   >[!NOTE]
   >
   >저장소를 추가하려면 사용자에게 **배포 관리자** 또는 **비즈니스 소유자** 역할이 있어야 합니다.

   ![저장소 추가](/help/assets/create-repo2.png)

1. 요청한 대로 이름과 설명을 입력하고 **저장**&#x200B;을 클릭합니다.

   ![저장소 세부 정보](/help/assets/repo-1.png)

1. **저장**&#x200B;을 선택합니다.

새로 생성한 저장소가 표시됩니다.

![새 저장소 생성됨](/help/assets/create-repo3.png)

Cloud Manager에서 만든 저장소는 [파이프라인을 만들](/help/overview/ci-cd-pipelines.md) 때 선택할 수 있습니다.

## 저장소 보기 및 편집 {#edit-repos}

다음 단계에 따라 Cloud Manager에서 저장소를 편집하고 볼 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **저장소** 탭을 클릭하고 **저장소** 페이지로 이동합니다. 여기서 기존 저장소의 세부 정보를 볼 수 있습니다.

1. 저장소를 선택하고 테이블 오른쪽 끝에 있는 줄임표 버튼을 클릭하여 **저장소 URL 복사** 또는 내 저장소 **보기 및 업데이트** 작업을 수행합니다.

![저장소 편집](/help/assets/create-repo3.png)

## 저장소 삭제 {#delete-repos}

저장소를 삭제하려면 [저장소 보기 및 편집](#edit-repos) 작업과 동일한 단계를 수행하되 **저장소** 페이지에서 삭제할 저장소의 줄임표 버튼을 클릭하고 **삭제**&#x200B;를 선택합니다.

저장소가 Cloud Manager에서 삭제되면 해당 저장소는 삭제된 것으로 표시되며 더 이상 사용자가 액세스할 수는 없지만 복구 목적으로 시스템에 유지됩니다.

저장소를 삭제한 후 동일한 이름으로 새 저장소를 생성하려고 하면 “저장소를 생성하는 도중 오류가 발생했습니다. CSE 또는 Adobe 지원 센터에 문의하십시오”라는 오류 메시지가 표시됩니다.

이 오류 메시지가 표시되면 Adobe 지원 센터에 문의하여 삭제된 저장소의 이름을 바꾸거나 새 저장소에 대해 다른 이름을 선택할 수 있도록 하십시오.

## git 하위 모듈 지원 {#git-submodule-support}

git 하위 모듈을 사용하여 빌드 시 git 저장소에 있는 여러 분기의 콘텐츠를 병합할 수 있습니다.

Cloud Manager의 빌드 프로세스가 실행되면 파이프라인에 대해 구성된 저장소를 복제하고 구성된 분기를 체크아웃한 후 분기의 루트 디렉터리에 `.gitmodules` 파일이 있으면 명령이 실행됩니다.

```
$ git submodule update --init
```

이렇게 하면 각 하위 모듈을 적절한 디렉터리로 체크아웃합니다. 이 기술은 [다중 소스 Git 저장소를 사용하여 작업](/help/managing-code/multiple-git-repos.md)에 대한 잠재적인 대안으로서, git 하위 모듈 사용에 익숙하고 외부 병합 프로세스를 관리하고 싶지 않은 조직에 적합합니다.

예를 들어 각각 `main`이라는 단일 분기를 포함하는 3개의 저장소가 있다고 가정해 보겠습니다. “기본 저장소”, 즉 파이프라인에 구성된 저장소에서 `main` 분기에는 다른 두 저장소에 포함된 프로젝트를 선언하는 `pom.xml` 파일이 있습니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
   
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
   
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
   
</project>
```

그런 다음 다른 두 저장소에 대한 하위 모듈을 추가합니다.

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

그러면 다음과 유사한 `.gitmodules` 파일이 생성됩니다.

```text
[submodule "project-a"]
    path = project-a
    url = https://git.cloudmanager.adobe.com/ProgramName/projectA/
    branch = main
[submodule "project-b"]
    path = project-b
    url = https://git.cloudmanager.adobe.com/ProgramName/projectB/
    branch = main
```

git 하위 모듈에 대한 자세한 내용은 [git 참조 설명서](https://git-scm.com/book/en/v2/Git-Tools-Submodules)에서 확인할 수 있습니다.

### 제한 사항 {#limitations}

git 하위 모듈을 사용할 때는 다음 사항에 유의하십시오.

* git URL은 위에서 설명한 구문과 정확히 일치해야 합니다.
* 보안상의 이유로 이러한 URL에 자격 증명을 임베드하지 마십시오.
* 분기의 루트에 있는 하위 모듈만 지원됩니다.
* git 하위 모듈 참조는 특정 git 커밋에 저장됩니다.
   * 결과적으로 하위 모듈 저장소가 변경되면 참조된 커밋을 업데이트해야 합니다. 예를 들어 `git submodule update --remote`를 사용합니다.
* 달리 필요한 경우가 아니면 “약식” 하위 모듈을 사용하는 것이 좋습니다.
   * 이렇게 하려면 각 하위 모듈에 대해 `git config -f .gitmodules submodule.<submodule path>.shallow true`를 실행합니다.
