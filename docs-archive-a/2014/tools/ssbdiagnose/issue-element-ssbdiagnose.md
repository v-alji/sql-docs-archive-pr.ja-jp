---
title: Issue 要素 (ssbdiagnose) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- issue element
- XML output file format [ssbdiagnose], issue element
- ssbdiagnose
ms.assetid: 2246a886-686b-44ca-9771-b155cedad8be
author: stevestein
ms.author: sstein
ms.openlocfilehash: a178c1323c1c20f84e67d4d7699fc313090a4c71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711210"
---
# <a name="issue-element-ssbdiagnose"></a><span data-ttu-id="51f0a-102">Issue 要素 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="51f0a-102">Issue Element (ssbdiagnose)</span></span>
  <span data-ttu-id="51f0a-103">**ssbdiagnose** ユーティリティによって検出された問題を報告します。</span><span class="sxs-lookup"><span data-stu-id="51f0a-103">Reports an issue that was found by the **ssbdiagnose** utility.</span></span> <span data-ttu-id="51f0a-104">**ssbdiagnose** の XML 出力ファイルには、報告される問題につき 1 つの Issue 要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="51f0a-104">The **ssbdiagnose** XML output file has one Issue element per issue reported.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51f0a-105">構文</span><span class="sxs-lookup"><span data-stu-id="51f0a-105">Syntax</span></span>  
  
```  
  
<Issue  
    type="..."   
    code="..."   
    server="..."   
    database="..."   
    object="...">   
    ...   
</Issue>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="51f0a-106">要素の属性</span><span class="sxs-lookup"><span data-stu-id="51f0a-106">Element Attributes</span></span>  
  
|<span data-ttu-id="51f0a-107">属性</span><span class="sxs-lookup"><span data-stu-id="51f0a-107">Attribute</span></span>|<span data-ttu-id="51f0a-108">説明</span><span class="sxs-lookup"><span data-stu-id="51f0a-108">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="51f0a-109">Issue 要素で報告する問題のカテゴリを次に示します。</span><span class="sxs-lookup"><span data-stu-id="51f0a-109">Identifies which category of problem the Issue element is reporting:</span></span><br /><br /> <span data-ttu-id="51f0a-110">**"Diagnosis"** では、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] の構成の分析時に検出された構成の問題を報告します。</span><span class="sxs-lookup"><span data-stu-id="51f0a-110">**"Diagnosis"** Reports a configuration issue found when you analyze a [!INCLUDE[ssSB](../../includes/sssb-md.md)] configuration.</span></span><br /><br /> <span data-ttu-id="51f0a-111">**"Problem"** では、 **ssbdiagnose** で分析を完了できない場合の原因となった問題を報告します。</span><span class="sxs-lookup"><span data-stu-id="51f0a-111">**"Problem"** Reports an issue that has prevented **ssbdiagnose** from completing its analysis.</span></span> <span data-ttu-id="51f0a-112">問題を修正して、 **ssbdiagnose**を再実行します。</span><span class="sxs-lookup"><span data-stu-id="51f0a-112">Correct the problem and rerun **ssbdiagnose**.</span></span><br /><br /> <span data-ttu-id="51f0a-113">**"Event"** では、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] -RUNTIME **チェックの実行時に検出された** イベントを報告します。</span><span class="sxs-lookup"><span data-stu-id="51f0a-113">**"Event"** Reports a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] event found when you run a **-RUNTIME** check.</span></span> <span data-ttu-id="51f0a-114">イベントが報告されるのは、 **-SHOWEVENTS** が指定されている場合のみです。</span><span class="sxs-lookup"><span data-stu-id="51f0a-114">Events are only reported if **-SHOWEVENTS** is specified.</span></span>|  
|`code`|<span data-ttu-id="51f0a-115">メッセージのエラー番号を示します。</span><span class="sxs-lookup"><span data-stu-id="51f0a-115">Identifies the error number for the message.</span></span>|  
|`server`|<span data-ttu-id="51f0a-116">問題が検出された [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスを示します。</span><span class="sxs-lookup"><span data-stu-id="51f0a-116">Identifies the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in which the problem was found.</span></span> <span data-ttu-id="51f0a-117">既定のインスタンスに問題があった場合、サーバー属性には、コンピューター名のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="51f0a-117">If the problem was in a default instance, the server attribute only has the computer name.</span></span> <span data-ttu-id="51f0a-118">既定のインスタンスに問題があった場合、サーバー属性は "ComputerName\ InstanceName" という形式になります。</span><span class="sxs-lookup"><span data-stu-id="51f0a-118">If the problem was in a named instance, the server attribute is in the form ComputerName\InstanceName.</span></span>|  
|`database`|<span data-ttu-id="51f0a-119">問題が検出されたデータベースの名前を示します。</span><span class="sxs-lookup"><span data-stu-id="51f0a-119">Identifies the name of the database in which the problem was found.</span></span>|  
|`object`|<span data-ttu-id="51f0a-120">問題が検出されたオブジェクトの名前を示します。</span><span class="sxs-lookup"><span data-stu-id="51f0a-120">Identifies the name of the object in which the problem was found.</span></span> <span data-ttu-id="51f0a-121">問題がインスタンス レベルまたはデータベース レベルの問題である場合、オブジェクト属性はインスタンス名またはデータベース名を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="51f0a-121">If the problem was an instance or database level issue, the object attribute repeats the instance or database name.</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="51f0a-122">要素の特性</span><span class="sxs-lookup"><span data-stu-id="51f0a-122">Element Characteristics</span></span>  
  
|<span data-ttu-id="51f0a-123">特徴</span><span class="sxs-lookup"><span data-stu-id="51f0a-123">Characteristic</span></span>|<span data-ttu-id="51f0a-124">説明</span><span class="sxs-lookup"><span data-stu-id="51f0a-124">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="51f0a-125">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="51f0a-125">**Data type and length**</span></span>|<span data-ttu-id="51f0a-126">`string`、長さは無制限です。</span><span class="sxs-lookup"><span data-stu-id="51f0a-126">`string`, length is unlimited.</span></span>|  
|<span data-ttu-id="51f0a-127">**Value**</span><span class="sxs-lookup"><span data-stu-id="51f0a-127">**Value**</span></span>|<span data-ttu-id="51f0a-128">エラー メッセージのテキストを返します。</span><span class="sxs-lookup"><span data-stu-id="51f0a-128">Returns the text of the error message.</span></span>|  
|<span data-ttu-id="51f0a-129">**個数**</span><span class="sxs-lookup"><span data-stu-id="51f0a-129">**Occurrence**</span></span>|<span data-ttu-id="51f0a-130">報告されたエラーにつき 1 個。</span><span class="sxs-lookup"><span data-stu-id="51f0a-130">Once per reported error.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="51f0a-131">要素の関係</span><span class="sxs-lookup"><span data-stu-id="51f0a-131">Element Relationships</span></span>  
  
|<span data-ttu-id="51f0a-132">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="51f0a-132">Relationship</span></span>|<span data-ttu-id="51f0a-133">要素</span><span class="sxs-lookup"><span data-stu-id="51f0a-133">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="51f0a-134">**親要素**</span><span class="sxs-lookup"><span data-stu-id="51f0a-134">**Parent element**</span></span>|[<span data-ttu-id="51f0a-135">DiagnosticInformation 要素 &#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="51f0a-135">DiagnosticInformation Element &#40;ssbdiagnose&#41;</span></span>](diagnosticinformation-element-ssbdiagnose.md)|  
|<span data-ttu-id="51f0a-136">**子要素**</span><span class="sxs-lookup"><span data-stu-id="51f0a-136">**Child elements**</span></span>|<span data-ttu-id="51f0a-137">なし</span><span class="sxs-lookup"><span data-stu-id="51f0a-137">None</span></span>|  
  
## <a name="example"></a><span data-ttu-id="51f0a-138">例</span><span class="sxs-lookup"><span data-stu-id="51f0a-138">Example</span></span>  
 <span data-ttu-id="51f0a-139">この要素は、マスター キーを持たないデータベースの 1102 エラーを報告します。このエラーは、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] の構成の分析時に検出されました。</span><span class="sxs-lookup"><span data-stu-id="51f0a-139">This element reports an 1102 error for a database that does not have a master key, where the error was found when you analyzed a [!INCLUDE[ssSB](../../includes/sssb-md.md)] configuration.</span></span>  
  
```  
<Issue type="Diagnosis" code="1102" server="TestComputer" database="TargetDB" object="TargetDB">The master key was not found</diagnostic>  
```  
  
## <a name="see-also"></a><span data-ttu-id="51f0a-140">参照</span><span class="sxs-lookup"><span data-stu-id="51f0a-140">See Also</span></span>  
 [<span data-ttu-id="51f0a-141">ssbdiagnose ユーティリティ &#40;Service Broker&#41;</span><span class="sxs-lookup"><span data-stu-id="51f0a-141">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](ssbdiagnose-utility-service-broker.md)  
  
  
