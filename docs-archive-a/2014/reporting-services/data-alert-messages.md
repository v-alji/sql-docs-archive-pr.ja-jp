---
title: データ警告メッセージ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6819720c-d848-4b90-9b51-89501b4f4645
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d50c3dd24c0057f695a9318c5eef7ad9e7540a45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642612"
---
# <a name="data-alert-messages"></a><span data-ttu-id="59b00-102">データ警告メッセージ</span><span class="sxs-lookup"><span data-stu-id="59b00-102">Data Alert Messages</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="59b00-103">データ警告は、2 種類のデータ警告メッセージを電子メールで配信します。データ警告結果を含むメッセージと、エラー説明を含むメッセージです。</span><span class="sxs-lookup"><span data-stu-id="59b00-103">data alerts deliver two types of data alert messages by email: Messages with data alert results and messages with error descriptions.</span></span> <span data-ttu-id="59b00-104">結果を含むメッセージは、すべての受信者に共通して関係し、かつ業務意思決定にとって重要なレポート データの変更について情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="59b00-104">Messages with results keep all recipients informed about changes in report data that is of common interest and important to business decisions.</span></span> <span data-ttu-id="59b00-105">何かの理由でエラーが発生し、結果情報が取得できない場合は、代わりにエラー メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="59b00-105">If for some reason an error occurs and the results are not available, the error message is sent instead.</span></span>

 <span data-ttu-id="59b00-106">データ警告定義の所有者は、データ警告マネージャーで、データ警告インスタンスに関する情報を参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="59b00-106">The owner of the data alert definition also can view information about the data alert instance in Data Alert Manager.</span></span> <span data-ttu-id="59b00-107">詳細については、「 [SharePoint ユーザー用のデータ警告マネージャー](../../2014/reporting-services/data-alert-manager-for-sharepoint-users.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59b00-107">For more information, see [Data Alert Manager for SharePoint Users](../../2014/reporting-services/data-alert-manager-for-sharepoint-users.md).</span></span>

##  <a name="data-alert-messages"></a><a name="DataAlertMessages"></a><span data-ttu-id="59b00-108">データ警告メッセージ</span><span class="sxs-lookup"><span data-stu-id="59b00-108">Data Alert Messages</span></span>
 <span data-ttu-id="59b00-109">次に示すのは、結果を含むデータ警告メッセージと、エラー説明を含む警告メッセージのスクリーン ショットです。</span><span class="sxs-lookup"><span data-stu-id="59b00-109">The following pictures show a data alert message with results and an alert message with an error description.</span></span>

 <span data-ttu-id="59b00-110">**結果メッセージ**</span><span class="sxs-lookup"><span data-stu-id="59b00-110">**Results message**</span></span>

 <span data-ttu-id="59b00-111">![結果を含むデータ警告の電子メール メッセージ](media/rs-alertmessageresults.gif "結果を含むデータ警告の電子メール メッセージ")</span><span class="sxs-lookup"><span data-stu-id="59b00-111">![Data alert e-mail message with results](media/rs-alertmessageresults.gif "Data alert e-mail message with results")</span></span>

 <span data-ttu-id="59b00-112">**エラー メッセージ**</span><span class="sxs-lookup"><span data-stu-id="59b00-112">**Error message**</span></span>

 <span data-ttu-id="59b00-113">![エラー メッセージを含むデータ警告メッセージ](media/rs-alertmessageerrror.gif "エラー メッセージを含むデータ警告メッセージ")</span><span class="sxs-lookup"><span data-stu-id="59b00-113">![Data alert message with error message](media/rs-alertmessageerrror.gif "Data alert message with error message")</span></span>

 <span data-ttu-id="59b00-114">これらのメッセージには、共通の情報項目が含まれます。</span><span class="sxs-lookup"><span data-stu-id="59b00-114">The messages include the same types of information.</span></span>

1.  <span data-ttu-id="59b00-115">**[代理]** には、データ警告定義の作成者の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="59b00-115">**On behalf of** contains the name of the person who created the data alert definition.</span></span>

2.  <span data-ttu-id="59b00-116">警告定義内に説明を入力した場合は、 **[代理]** の下に説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="59b00-116">If you provided a description in the alert definition, it displays below **On behalf of**.</span></span>

3.  <span data-ttu-id="59b00-117">**[警告結果]** には、警告定義で指定されたルールを満たすレポート データ フィード内の行が表形式で表示されるか、またはエラー説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="59b00-117">**Alert Results** display the rows in the report data feed that satisfy the rules specified in the alert definition in a tabular format or display an error description.</span></span> <span data-ttu-id="59b00-118">表示される行数に制限はありません。</span><span class="sxs-lookup"><span data-stu-id="59b00-118">There is no limit on the number of rows that displays.</span></span>

4.  <span data-ttu-id="59b00-119">**[レポートに移動する]** は、警告定義の作成対象であるレポートへのリンクです。</span><span class="sxs-lookup"><span data-stu-id="59b00-119">**Go to report** is a link to the report that the alert definition is built upon.</span></span> <span data-ttu-id="59b00-120">レポートが移動または削除されたためにリンクが無効になっている場合は、エラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="59b00-120">If the link is not valid because the report was moved or deleted, an error message displays.</span></span>

5.  <span data-ttu-id="59b00-121">**[ルール]** には、警告定義内のルールと句がリストされます。</span><span class="sxs-lookup"><span data-stu-id="59b00-121">**Rule(s)** lists the rules and clauses in the alert definition.</span></span> <span data-ttu-id="59b00-122">この情報は、警告結果を検証および理解したり、変更したい警告定義内のルールを識別して、結果の範囲を絞り込んだり広げたりするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="59b00-122">This information helps you verify and understand the alert results and identify rules in the data alert definition that you might want to change to narrow or broaden results.</span></span>

6.  <span data-ttu-id="59b00-123">**[レポート パラメーター]** には、レポートの実行時に使用されたパラメーターとパラメーター値がリストされます。</span><span class="sxs-lookup"><span data-stu-id="59b00-123">**Report parameters** list the parameters and parameter values that were used when the report was run.</span></span> <span data-ttu-id="59b00-124">パラメーターとパラメーター値は、警告結果を理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="59b00-124">Parameters and parameter values help you understand the alert results.</span></span>

7.  <span data-ttu-id="59b00-125">**[コンテキスト値]** には、レポート データ領域の外部にあるレポート アイテムの名前と値がリストされます。</span><span class="sxs-lookup"><span data-stu-id="59b00-125">**Contextual values** list the names and values of report items that are outside of the report data regions.</span></span> <span data-ttu-id="59b00-126">これらのアイテムは通常、テキスト ボックスです。</span><span class="sxs-lookup"><span data-stu-id="59b00-126">The items are typically text boxes.</span></span> <span data-ttu-id="59b00-127">たとえば、定数値 (レポートの件名や説明など) を格納したテキスト ボックスなどが該当します。</span><span class="sxs-lookup"><span data-stu-id="59b00-127">For example, a text box with a constant value such as the subject or description of a report.</span></span>

 <span data-ttu-id="59b00-128">2 つのメッセージ型の間で唯一異なるのは、項目 5 ( **警告結果**) です。</span><span class="sxs-lookup"><span data-stu-id="59b00-128">The only difference between the two message types is item 5, **Alert Results**.</span></span> <span data-ttu-id="59b00-129">データ警告インスタンスまたはデータ警告メッセージの作成時にエラーが発生した場合は、問題を説明するエラー メッセージが **[警告結果]** に表示されます。</span><span class="sxs-lookup"><span data-stu-id="59b00-129">If an error occurs when a data alert instance or data alert message is created, **Alert Results** displays an error message that describes the problem.</span></span> <span data-ttu-id="59b00-130">エラー メッセージ (すべての受信者に送信される) は、業務上の意思決定に有効または必要な警告結果が利用できないことを受信者に知らせます。</span><span class="sxs-lookup"><span data-stu-id="59b00-130">The error message, sent to all recipients, let them know that the alert results that they are expecting and might rely on to make business decisions are not available.</span></span>

 

##  <a name="related-tasks"></a><a name="HowTo"></a> <span data-ttu-id="59b00-131">関連タスク</span><span class="sxs-lookup"><span data-stu-id="59b00-131">Related Tasks</span></span>
 <span data-ttu-id="59b00-132">データ警告メッセージ内に表示される情報の多くを提供する、データ警告定義を作成および編集するための手順を紹介しているトピックの一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="59b00-132">This section lists procedures that show you how to create and edit the data alert definitions that provide much of the information that you see in data alert messages.</span></span>

-   [<span data-ttu-id="59b00-133">警告デザイナーでのデータ警告の作成</span><span class="sxs-lookup"><span data-stu-id="59b00-133">Create a Data Alert in Data Alert Designer</span></span>](create-a-data-alert-in-data-alert-designer.md)

-   [<span data-ttu-id="59b00-134">警告デザイナーでのデータ警告の編集</span><span class="sxs-lookup"><span data-stu-id="59b00-134">Edit a Data Alert in Alert Designer</span></span>](edit-a-data-alert-in-alert-designer.md)



## <a name="see-also"></a><span data-ttu-id="59b00-135">参照</span><span class="sxs-lookup"><span data-stu-id="59b00-135">See Also</span></span>
 <span data-ttu-id="59b00-136">データ[警告デザイナー](../../2014/reporting-services/data-alert-designer.md)の[Reporting Services データ警告](../ssms/agent/alerts.md)</span><span class="sxs-lookup"><span data-stu-id="59b00-136">[Data Alert Designer](../../2014/reporting-services/data-alert-designer.md) [Reporting Services Data Alerts](../ssms/agent/alerts.md)</span></span>


