---
title: Cloud Manager 저장소
description: Cloud Manager 프로그램의 리포지토리에 액세스, 생성 및 편집하는 방법을 알아봅니다.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 2%

---


# Cloud Manager 저장소 {#cloud-manager-repos}

리포지토리는 git을 사용하여 코드를 관리하는 곳입니다. Cloud Manager 프로그램용 저장소를 만드는 방법을 알아봅니다.

## 저장소에 액세스 {#accessing-repos}

Cloud Manager에서 셀프 서비스에서 Git 리포지토리에 액세스하고 관리할 수 있습니다.

리포지토리에 액세스하려면 **보고서 정보에 액세스** 대부분의 경우 파이프라인 카드에서 Cloud Manager에서 사용할 수 있는 단추입니다.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) 적절한 조직과 프로그램을 선택합니다.

1. 다음으로 이동 **파이프라인** 카드로부터 **프로그램 개요** 페이지를 보면 **보고서 정보에 액세스** git 리포지토리 액세스 및 관리 옵션 [이 파이프라인으로 구성되었습니다.](/help/using/production-pipelines.md)

   ![보고서 정보 액세스 단추](/help/assets/access-repo1.png)

1. 로 전환하는 경우 **비프로덕션** 파이프라인 탭, **보고서 정보에 액세스** 옵션도 [파이프라인에 대해 구성되었습니다.](/help/using/non-production-pipelines.md)

   ![비프로덕션 파이프라인](/help/assets/access-repo-nonprod.png)

1. 을(를) 클릭합니다. **보고서 정보에 액세스** 단추를 클릭하여 표시되는 대화 상자를 엽니다.

   * Git 리포지토리의 URL
   * 사용자 이름
   * 암호
   * 로컬로 리포지토리를 복제하기 위해 실행하는 Git 명령

   ![저장소 정보 대화 상자](/help/assets/access-repo-create.png)

제공된 정보를 사용하여 로컬 개발을 시작할 수 있도록 리포지토리를 로컬로 복제합니다.

>[!NOTE]
>
>다음 **보고서 정보에 액세스** 옵션을 볼 수 있습니다 **개발자** 또는 **배포 관리자** 역할.

## 저장소 추가 {#add-repos}

Cloud Manager에서 저장소를 추가하려면 다음 단계를 수행합니다.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) 적절한 조직과 프로그램을 선택합니다.

1. 에서 **프로그램 개요** 페이지를 클릭합니다. **저장소** 탭을 클릭하고 **저장소** 페이지.

1. 클릭 **저장소 추가** 마법사를 시작하려면 다음을 수행하십시오.

   >[!NOTE]
   >
   >다음 항목이 있어야 합니다. **배포 관리자** 또는 **비즈니스 소유자** 저장소를 추가할 역할입니다.

   ![저장소 추가](/help/assets/create-repo2.png)

1. 원하는 이름과 설명을 입력하고 을(를) 클릭합니다 **저장**.

   ![보고서 세부 정보](/help/assets/repo-1.png)

1. **저장**&#x200B;을 선택합니다.

새로 만든 보고서가 표시됩니다.

![새 보고서가 생성됨](/help/assets/create-repo3.png)

Cloud Manager에서 만든 리포지토리는 다음 경우에 선택할 수 있습니다 [파이프라인을 만듭니다.](/help/overview/ci-cd-pipelines.md)

## 저장소 보기 및 편집 {#edit-repos}

Cloud Manager에서 리포지토리를 편집하고 보려면 다음 단계를 따르십시오.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) 적절한 조직과 프로그램을 선택합니다.

1. 에서 **프로그램 개요** 페이지를 클릭합니다. **저장소** 탭을 클릭하고 **저장소** 페이지. 여기에서 기존 리포지토리의 세부 정보를 볼 수 있습니다.

1. 저장소를 선택하고 표의 맨 오른쪽에 있는 줄임표 단추를 누릅니다 **저장소 URL 복사**, **보기 및 업데이트** 또는 **삭제** 리포지토리.

![보고서 편집](/help/assets/create-repo3.png)

## Git 하위 모듈 지원 {#git-submodule-support}

Git 하위 모듈을 사용하여 빌드 시 Git 리포지토리에서 여러 분기의 콘텐츠를 병합할 수 있습니다.

Cloud Manager의 빌드 프로세스가 실행될 때 분기에 가 포함되어 있으면 파이프라인에 대해 구성된 리포지토리를 복제하고 구성된 분기를 체크 아웃한 후 `.gitmodules` 루트 디렉토리에 있는 파일에서 명령이 실행됩니다.

```
$ git submodule update --init
```

이렇게 하면 각 하위 모듈이 해당 디렉토리에 체크 아웃됩니다. 이 기술은 [여러 소스 Git 리포지토리 작업](/help/managing-code/multiple-git-repos.md) git 하위 모듈 사용에 익숙하며 외부 병합 프로세스를 관리하지 않으려는 조직의 경우.

예를 들어 세 개의 리포지토리가 있으며, 각 리포지토리는 이름이 인 단일 분기를 포함합니다 `main`. &quot;기본&quot; 저장소에서, 즉 파이프라인에 구성된 저장소입니다. `main` 분기에는 `pom.xml` 다른 두 저장소에 포함된 프로젝트를 선언하는 파일:

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

이 경우 `.gitmodules` 파일 형식:

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

Git 하위 모듈에 대한 자세한 내용은 [Git 참조 설명서](https://git-scm.com/book/en/v2/Git-Tools-Submodules).

### 제한 사항 {#limitations}

Git 하위 모듈을 사용할 때는 다음 사항에 유의하십시오.

* Git URL은 위에서 설명한 구문에 정확히 포함되어야 합니다.
* 보안상의 이유로 이러한 URL에 자격 증명을 포함하지 마십시오.
* 분기의 루트에 있는 하위 모듈만 지원됩니다.
* Git 하위 모듈 참조는 특정 Git 커밋에 저장됩니다.
   * 따라서 하위 모듈 리포지토리를 변경할 때 예를 들어, 를 사용하여 커밋 참조 사항을 업데이트해야 합니다 `git submodule update --remote`.
* 별도로 필요하지 않는 한 &quot;얕은&quot; 하위 모듈을 사용하는 것이 좋습니다.
   * 이렇게 하려면 를 실행합니다. `git config -f .gitmodules submodule.<submodule path>.shallow true` 각 하위 모듈용.
