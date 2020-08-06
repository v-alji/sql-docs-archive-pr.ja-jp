---
title: ドメインの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.createdomain.f1
ms.assetid: 5c4828f5-bd51-4c29-b3de-87b7d2f2d3e5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fad6abd795aa9412bb71d251623d92d3e13b889c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632726"
---
# <a name="create-a-domain"></a><span data-ttu-id="519fa-102">ドメインの作成</span><span class="sxs-lookup"><span data-stu-id="519fa-102">Create a Domain</span></span>
  <span data-ttu-id="519fa-103">このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) でドメインを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="519fa-103">This topic describes how to create a domain in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="519fa-104">ドメインの値は、フィールド内のデータのセマンティック表現です。</span><span class="sxs-lookup"><span data-stu-id="519fa-104">The values in the domain are a semantic representation of the data in a field.</span></span> <span data-ttu-id="519fa-105">ドメインについて詳しくは、「[ドメインの管理](../../2014/data-quality-services/managing-a-domain.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="519fa-105">For more information on domains, see [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md).</span></span>  
  
 <span data-ttu-id="519fa-106">新しいドメインを作成するには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="519fa-106">There are two ways to create a new domain.</span></span> <span data-ttu-id="519fa-107">1 つ目は、ナレッジ検出アクティビティのマップ手順中に、データ サンプルを分析する過程でナレッジを新しいまたは既存のナレッジ ベースに追加するときに行います。</span><span class="sxs-lookup"><span data-stu-id="519fa-107">The first is during the Map step of the knowledge discovery activity, when you are in the process of analyzing a data sample to add knowledge to a new or existing knowledge base.</span></span> <span data-ttu-id="519fa-108">2 つ目は、ドメイン管理アクティビティの実行中に、既存のドメインを変更するのではなく、新しいドメインを作成するときに行います。</span><span class="sxs-lookup"><span data-stu-id="519fa-108">The second is during the domain management activity, when instead of changing an existing domain, you create a new one.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="519fa-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="519fa-109">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="519fa-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="519fa-110">Prerequisites</span></span>  
 <span data-ttu-id="519fa-111">ドメインを作成するには、ナレッジ ベースを作成して開いておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="519fa-111">To create a domain, you must have created and opened a knowledge base.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="519fa-112">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="519fa-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="519fa-113">Permissions</span><span class="sxs-lookup"><span data-stu-id="519fa-113">Permissions</span></span>  
 <span data-ttu-id="519fa-114">ドメインを作成するには、DQS_MAIN データベースの dqs_kb_editor ロールまたは dqs_administrator が必要です。</span><span class="sxs-lookup"><span data-stu-id="519fa-114">You must have the dqs_kb_editor role or the dqs_administrator on the DQS_MAIN database to create a domain.</span></span>  
  
##  <a name="create-a-domain-in-the-knowledge-discovery-activity"></a><a name="Discovery"></a><span data-ttu-id="519fa-115">ナレッジ検出アクティビティでのドメインの作成</span><span class="sxs-lookup"><span data-stu-id="519fa-115">Create a Domain in the Knowledge Discovery Activity</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="519fa-116">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="519fa-116">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="519fa-117">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、 **[ナレッジ ベースを開く]** をクリックし、ナレッジ ベースを選択するか、 **[新しいナレッジ ベース]** をクリックし、新しいナレッジ ベースのプロパティを入力します。</span><span class="sxs-lookup"><span data-stu-id="519fa-117">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open knowledge base** and then select a knowledge base, or click **New knowledge base** and enter properties for the new knowledge base.</span></span>  
  
3.  <span data-ttu-id="519fa-118">アクティビティとして **[ナレッジ検出]** を選択した後に、 **[作成]** をクリックして新しいナレッジ ベースを作成するか、 **[開く]** をクリックして既存のナレッジ ベースを開きます。</span><span class="sxs-lookup"><span data-stu-id="519fa-118">Select **Knowledge Discovery** as the activity, and then click **Create** to create the new knowledge base or **Open** to open an existing knowledge base.</span></span>  
  
4.  <span data-ttu-id="519fa-119">**[マップ]** ページで、データ ソースへの接続を指定します。</span><span class="sxs-lookup"><span data-stu-id="519fa-119">On the **Map** page, specify a connection to the data source.</span></span> <span data-ttu-id="519fa-120">詳細については、「 [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="519fa-120">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md).</span></span>  
  
5.  <span data-ttu-id="519fa-121">**"マッピング"** テーブルで、空の行の **[ソース列]** 列のドロップダウン リストからソース列を選択します。</span><span class="sxs-lookup"><span data-stu-id="519fa-121">In the **Mappings** table, select a source column from the drop-down list for the **Source Column** column of an empty row.</span></span> <span data-ttu-id="519fa-122">対応するドメインが存在しない場合は、 **[ドメインの作成]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="519fa-122">If no corresponding domain exists, click the **Create a Domain** icon.</span></span>  
  
##  <a name="create-a-domain-in-the-domain-management-activity"></a><a name="DomainManagement"></a><span data-ttu-id="519fa-123">ドメイン管理アクティビティでドメインを作成する</span><span class="sxs-lookup"><span data-stu-id="519fa-123">Create a Domain in the Domain Management Activity</span></span>  
  
1.  <span data-ttu-id="519fa-124">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、 **[ナレッジ ベースを開く]** をクリックし、ナレッジ ベースを選択するか、 **[新しいナレッジ ベース]** をクリックし、新しいナレッジ ベースのプロパティを入力します。</span><span class="sxs-lookup"><span data-stu-id="519fa-124">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open knowledge base** and then select a knowledge base, or click **New knowledge base** and enter properties for the new knowledge base.</span></span>  
  
2.  <span data-ttu-id="519fa-125">アクティビティとして **[ドメイン管理]** を選択した後に、 **[作成]** をクリックして新しいナレッジ ベースを作成するか、 **[開く]** をクリックして既存のナレッジ ベースを開きます。</span><span class="sxs-lookup"><span data-stu-id="519fa-125">Select **Domain Management** as the activity, and then click **Create** to create the new knowledge base or **Open** to open an existing knowledge base.</span></span>  
  
3.  <span data-ttu-id="519fa-126">**[ドメイン管理]** ページで、ドメイン リストの上にある **[ドメインの作成]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="519fa-126">On the **Domain Management** page, click the **Create a Domain** icon above the Domain list.</span></span>  
  
##  <a name="set-domain-properties"></a><a name="Properties"></a><span data-ttu-id="519fa-127">ドメインのプロパティの設定</span><span class="sxs-lookup"><span data-stu-id="519fa-127">Set Domain Properties</span></span>  
  
1.  <span data-ttu-id="519fa-128">**[ドメインの作成]** ダイアログ ボックスで、ナレッジ ベースに一意の名前と 256 文字までの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="519fa-128">In the **Create Domain** dialog box, enter a name that is unique to the knowledge base and a description up to 256 characters.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="519fa-129">ドメインのプロパティの詳細については、「 [Set Domain Properties](../../2014/data-quality-services/set-domain-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="519fa-129">For more information about domain properties, see [Set Domain Properties](../../2014/data-quality-services/set-domain-properties.md).</span></span>  
  
2.  <span data-ttu-id="519fa-130">**[データ型]** の一覧で、ドメイン内の値に対するデータ型を選択します。</span><span class="sxs-lookup"><span data-stu-id="519fa-130">From the **Data Type** list, select a data type for the values in the domain.</span></span> <span data-ttu-id="519fa-131">データ型には、 **[String]** (既定値)、 **[Date]**、 **[Integer]**、または **[Decimal]** を指定できます。</span><span class="sxs-lookup"><span data-stu-id="519fa-131">The data type can be **String** (the default), **Date**, **Integer**, or **Decimal**.</span></span>  
  
3.  <span data-ttu-id="519fa-132">シノニムの値ではなく、シノニムのグループの先頭の値が出力されることを指定する場合は、 **[先頭の値を使用]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="519fa-132">Select **Use Leading Values** to specify that the leading value in a group of synonyms will be output instead of a value that is a synonym to it.</span></span> <span data-ttu-id="519fa-133">各シノニムの値が正しいフォームまたは修正されたフォームで出力され、そのグループの先頭の値で置き換えられないことを指定する場合は、 **[先頭の値を使用]** をオフにします。</span><span class="sxs-lookup"><span data-stu-id="519fa-133">Deselect **Use Leading Values** to specify that each synonym value is output in its correct or corrected form, and is not replaced by the leading value for its group.</span></span>  
  
4.  <span data-ttu-id="519fa-134">データ型が **[String]** の場合は、 **[文字列を正規化する]** をオンにしてドメイン値の特殊文字を削除すると、一致の可能性が高まる場合があります。</span><span class="sxs-lookup"><span data-stu-id="519fa-134">If the data type is **String**, select **Normalize String** to remove special characters in the domain values, which may improve the likelihood of matches.</span></span>  
  
5.  <span data-ttu-id="519fa-135">**[形式の出力先]** ボックスの一覧で、ドメイン内のデータ値が出力されるときに適用される書式設定を選択します。</span><span class="sxs-lookup"><span data-stu-id="519fa-135">From the **Format Output to** drop-down list, select the formatting that will be applied when the data values in the domain are output.</span></span> <span data-ttu-id="519fa-136">書式設定は、次の一覧に示すように手順 2. で選択されたデータ型に固有です。</span><span class="sxs-lookup"><span data-stu-id="519fa-136">The formatting is specific to the data type selected in step 2, as shown in the following list:</span></span>  
  
    -   <span data-ttu-id="519fa-137">文字列値の場合は、出力する文字列を大文字、小文字、または先頭文字のみ大文字として指定できます。</span><span class="sxs-lookup"><span data-stu-id="519fa-137">For a string value, you can specify that the string be output as upper case, lower case, or capitalized.</span></span>  
  
    -   <span data-ttu-id="519fa-138">日付値の場合は、日、月、および年の形式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="519fa-138">For a date value, you can specify the format of the day, month, and year.</span></span>  
  
    -   <span data-ttu-id="519fa-139">整数値の場合は、適用される形式マスクの種類を指定できます。</span><span class="sxs-lookup"><span data-stu-id="519fa-139">For an integer value, you can specify the type of format mask to be applied.</span></span>  
  
    -   <span data-ttu-id="519fa-140">10 進数値の場合は、適用される精度と形式マスクの種類を指定できます。</span><span class="sxs-lookup"><span data-stu-id="519fa-140">For a decimal value, you can specify the accuracy and the type of format mask to be applied.</span></span>  
  
     <span data-ttu-id="519fa-141">**[形式の出力先]** ボックスで **[なし]** をクリックすると、一覧のどの書式設定も適用されません。</span><span class="sxs-lookup"><span data-stu-id="519fa-141">Selecting **None** in the **Format Output to** drop-down list means none of the formats in the list will be applied.</span></span>  
  
6.  <span data-ttu-id="519fa-142">データ型が **[String]** の場合は、 **[言語]** ボックスの一覧で、スペル チェックを有効にした場合に適用するスペル チェックの言語バージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="519fa-142">If the data type is **String**, in the **Language** drop-down list, select which language version of the speller you want to apply if you enable the speller.</span></span>  
  
7.  <span data-ttu-id="519fa-143">データ型が **[String]** の場合は、 **[スペル チェックを有効にする]** をオンにして、ドメインを設定するときにすべての文字列値に対してスペル チェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="519fa-143">If the data type is **String**, select **Enable Speller** to run the Speller on all string values when populating the domain.</span></span>  
  
8.  <span data-ttu-id="519fa-144">データ型が **[String]** の場合は、 **[構文エラーのアルゴリズムを無効にする]** をオンにして、文字列値の構文エラーをチェックせずにドメインを設定します。</span><span class="sxs-lookup"><span data-stu-id="519fa-144">If the data type is **String**, select **Disable Syntax Error Algorithms** to populate the domain without checking string values for syntax errors.</span></span>  
  
9. <span data-ttu-id="519fa-145">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="519fa-145">Click **OK**.</span></span>  
  
10. <span data-ttu-id="519fa-146">**[完了]** をクリックし、「 [ドメイン管理アクティビティの終了](../../2014/data-quality-services/end-the-domain-management-activity.md)」の説明に従ってドメイン管理アクティビティを完了します。</span><span class="sxs-lookup"><span data-stu-id="519fa-146">Click **Finish** to complete the domain management activity, as described in [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md).</span></span>  
  
##  <a name="follow-up-after-creating-a-domain"></a><a name="FollowUp"></a><span data-ttu-id="519fa-147">補足情報: ドメインを作成した後</span><span class="sxs-lookup"><span data-stu-id="519fa-147">Follow Up: After Creating a Domain</span></span>  
 <span data-ttu-id="519fa-148">ドメインを作成した後、ドメインで他のドメイン管理タスクを実行したり、ナレッジ検出を実行してナレッジをドメインに追加したり、照合ポリシーをドメインに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="519fa-148">After you create a domain, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="519fa-149">詳しくは、「[ナレッジ検出の実行](../../2014/data-quality-services/perform-knowledge-discovery.md)」、「[ドメインの管理](../../2014/data-quality-services/managing-a-domain.md)」、または「[照合ポリシーの作成](../../2014/data-quality-services/create-a-matching-policy.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="519fa-149">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
  
