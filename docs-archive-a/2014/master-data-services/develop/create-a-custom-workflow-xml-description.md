---
title: カスタム ワークフロー XML の説明 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: e267e5f4-38bb-466d-82e8-871eabeec07e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 77906426ddb901ec422367bf30aabef2e532ad06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646187"
---
# <a name="custom-workflow-xml-description-master-data-services"></a><span data-ttu-id="1d453-102">カスタム ワークフロー XML の説明 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1d453-102">Custom Workflow XML Description (Master Data Services)</span></span>
  <span data-ttu-id="1d453-103">では、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] ワークフローの開始時に、SQL SERVER MDS Workflow Integration Service によって、 [MasterDataServices \*](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130))メソッドが呼び出されています。</span><span class="sxs-lookup"><span data-stu-id="1d453-103">In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], the [Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow\*](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) method is called by SQL Server MDS Workflow Integration Service when a workflow starts.</span></span> <span data-ttu-id="1d453-104">このメソッドは、ワークフロー ビジネス ルールをトリガーしたアイテムに関するメタデータとデータを、XML のブロックとして受け取ります。</span><span class="sxs-lookup"><span data-stu-id="1d453-104">This method receives metadata and data about the item that triggered the workflow business rule as a block of XML.</span></span> <span data-ttu-id="1d453-105">ワークフロー ハンドラーを実装するコードの例については、「[カスタム ワークフローの例 &#40;マスター データ サービス&#41;](create-a-custom-workflow-example.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d453-105">For example code that implements a workflow handler, see [Custom Workflow Example &#40;Master Data Services&#41;](create-a-custom-workflow-example.md).</span></span>  
  
 <span data-ttu-id="1d453-106">次の例は、ワークフロー ハンドラーに送られる XML の内容を示したものです。</span><span class="sxs-lookup"><span data-stu-id="1d453-106">The following example shows what the XML that is sent to the workflow handler might look like:</span></span>  
  
```scr  
<ExternalAction>  
  <Type>TEST</Type>  
  <SendData>1</SendData>  
  <Server_URL>This is my test!</Server_URL>  
  <Action_ID>Test Workflow</Action_ID>  
  <Model_ID>5</Model_ID>  
  <Model_Name>Customer</Model_Name>  
  <Entity_ID>34</Entity_ID>  
  <Entity_Name>Customer</Entity_Name>  
  <Version_ID>8</Version_ID>  
  <MemberType_ID>1</MemberType_ID>  
  <Member_ID>12</Member_ID>  
  <MemberData>  
    <ID>12</ID>  
    <Version_ID>8</Version_ID>  
    <ValidationStatus_ID>3</ValidationStatus_ID>  
    <ChangeTrackingMask>0</ChangeTrackingMask>  
    <EnterDTM>2011-02-25T20:16:36.650</EnterDTM>  
    <EnterUserID>2</EnterUserID>  
    <EnterUserName>MyUserName</EnterUserName>  
    <EnterUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</EnterUserMuid>  
    <EnterVersionId>8</EnterVersionId>  
    <EnterVersionName>VERSION_1</EnterVersionName>  
    <EnterVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</EnterVersionMuid>  
    <LastChgDTM>2011-02-25T20:16:36.650</LastChgDTM>  
    <LastChgUserID>2</LastChgUserID>  
    <LastChgUserName>MyUserName</LastChgUserName>  
    <LastChgUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</LastChgUserMuid>  
    <LastChgVersionId>8</LastChgVersionId>  
    <LastChgVersionName>VERSION_1</LastChgVersionName>  
    <LastChgVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</LastChgVersionMuid>  
    <Name>Test Customer</Name>  
    <Code>TC</Code>  
  </MemberData>  
</ExternalAction>  
```  
  
 <span data-ttu-id="1d453-107">次の表に、この XML に含まれるタグの一部を示します。</span><span class="sxs-lookup"><span data-stu-id="1d453-107">The following table describes some of the tags contained in this XML:</span></span>  
  
|<span data-ttu-id="1d453-108">タグ</span><span class="sxs-lookup"><span data-stu-id="1d453-108">Tag</span></span>|<span data-ttu-id="1d453-109">説明</span><span class="sxs-lookup"><span data-stu-id="1d453-109">Description</span></span>|  
|---------|-----------------|  
|\<Type>|<span data-ttu-id="1d453-110">どのカスタム ワークフロー アセンブリを読み込むかを識別するために、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] の **[ワークフローの種類]** ボックスに入力したテキスト。</span><span class="sxs-lookup"><span data-stu-id="1d453-110">The text you entered in the **Workflow type** text box in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] to identify which custom workflow assembly to load.</span></span>|  
|\<SendData>|<span data-ttu-id="1d453-111">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] の **[メッセージにメンバーのデータを含める]** チェック ボックスによって制御されるブール値。</span><span class="sxs-lookup"><span data-stu-id="1d453-111">A Boolean value controlled by the **Include member data in the message** checkbox in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span> <span data-ttu-id="1d453-112">値1は、セクションが送信されることを意味します。 \<MemberData> それ以外の場合は、 \<MemberData> セクションは送信されません。</span><span class="sxs-lookup"><span data-stu-id="1d453-112">A value of 1 means that the \<MemberData> section is sent; otherwise the \<MemberData> section is not sent.</span></span>|  
|<span data-ttu-id="1d453-113"><Server_URL></span><span class="sxs-lookup"><span data-stu-id="1d453-113"><Server_URL></span></span>|<span data-ttu-id="1d453-114">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] の **[ワークフロー サイト]** ボックスに入力したテキスト。</span><span class="sxs-lookup"><span data-stu-id="1d453-114">The text you entered in the **Workflow site** text box in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span>|  
|<span data-ttu-id="1d453-115"><Action_ID></span><span class="sxs-lookup"><span data-stu-id="1d453-115"><Action_ID></span></span>|<span data-ttu-id="1d453-116">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] の **[ワークフロー名]** ボックスに入力したテキスト。</span><span class="sxs-lookup"><span data-stu-id="1d453-116">The text you entered in the **Workflow name** text box in [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span>|  
|\<MemberData>|<span data-ttu-id="1d453-117">ワークフロー アクションをトリガーしたメンバーのデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1d453-117">Contains the data of the member that triggered the workflow action.</span></span> <span data-ttu-id="1d453-118">この値は、の値が1の場合にのみ含まれ \<SendData> ます。</span><span class="sxs-lookup"><span data-stu-id="1d453-118">This is included only if the value of \<SendData> is 1.</span></span>|  
|\<Enter*xxx*>|<span data-ttu-id="1d453-119">このタグ セットには、メンバーの作成に関するメタデータ (作成日時や作成者など) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1d453-119">This set of tags contains metadata about the creation of the member, such as when it was created and who created it.</span></span>|  
|\<LastChg*xxx*>|<span data-ttu-id="1d453-120">このタグ セットには、メンバーへの最終変更に関するメタデータ (変更日時や変更者など) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1d453-120">This set of tags contains metadata about the last change made to the member, such as when the change was made and who made it.</span></span>|  
|\<Name>|<span data-ttu-id="1d453-121">変更されたメンバーの最初の属性。</span><span class="sxs-lookup"><span data-stu-id="1d453-121">The first attribute of the member that was changed.</span></span> <span data-ttu-id="1d453-122">この例のメンバーには、Name 属性と Code 属性のみが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1d453-122">This example member contains only Name and Code attributes.</span></span>|  
|\<Code>|<span data-ttu-id="1d453-123">変更されたメンバーの次の属性。</span><span class="sxs-lookup"><span data-stu-id="1d453-123">The next attribute of the member that was changed.</span></span> <span data-ttu-id="1d453-124">この例のメンバーにさらに多くの属性が含まれていた場合、それらはこのタグの後に続きます。</span><span class="sxs-lookup"><span data-stu-id="1d453-124">If this example member contained more attributes, they would follow this one.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d453-125">参照</span><span class="sxs-lookup"><span data-stu-id="1d453-125">See Also</span></span>  
 <span data-ttu-id="1d453-126">[カスタムワークフロー &#40;マスターデータサービスの作成&#41;](create-a-custom-workflow-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="1d453-126">[Create a Custom Workflow &#40;Master Data Services&#41;](create-a-custom-workflow-master-data-services.md) </span></span>  
 [<span data-ttu-id="1d453-127">カスタム ワークフローの例 &#40;マスター データ サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="1d453-127">Custom Workflow Example &#40;Master Data Services&#41;</span></span>](create-a-custom-workflow-example.md)  
  
  
