---
title: データ警告デザイナーでのデータ警告の作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8464ab9d-afe1-4490-955f-9f3319bcbf8d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 19c3001d4663848c009a353baa068f237d4a0b5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719719"
---
# <a name="create-a-data-alert-in-data-alert-designer"></a><span data-ttu-id="2dcce-102">警告デザイナーでのデータ警告の作成</span><span class="sxs-lookup"><span data-stu-id="2dcce-102">Create a Data Alert in Data Alert Designer</span></span>
  <span data-ttu-id="2dcce-103">データ警告の定義は、データ警告デザイナーで作成します。</span><span class="sxs-lookup"><span data-stu-id="2dcce-103">You create data alert definitions in Data Alert Designer.</span></span> <span data-ttu-id="2dcce-104">作成した警告定義は、保存後、再度データ警告デザイナーで開いて編集し、保存し直すことができます。</span><span class="sxs-lookup"><span data-stu-id="2dcce-104">After you save the alert definitions, you can reopen, edit, and then resave them in Data Alert Designer.</span></span> <span data-ttu-id="2dcce-105">警告定義の編集の詳細については、「 [データ警告マネージャーでのデータ警告の管理](manage-my-data-alerts-in-data-alert-manager.md) 」および「 [警告デザイナーでのデータ警告の編集](edit-a-data-alert-in-alert-designer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dcce-105">For information about editing alert definitions, see [Manage My Data Alerts in Data Alert Manager](manage-my-data-alerts-in-data-alert-manager.md) and [Edit a Data Alert in Alert Designer](edit-a-data-alert-in-alert-designer.md).</span></span>

### <a name="to-create-a-data-alert-definition"></a><span data-ttu-id="2dcce-106">データ警告の定義を作成するには</span><span class="sxs-lookup"><span data-stu-id="2dcce-106">To create a data alert definition</span></span>

1.  <span data-ttu-id="2dcce-107">データ警告定義の作成対象となるレポートを含んだ SharePoint ライブラリを探します。</span><span class="sxs-lookup"><span data-stu-id="2dcce-107">Locate the SharePoint library that contains the report that you want to create a data alert definition for.</span></span>

2.  <span data-ttu-id="2dcce-108">レポートをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dcce-108">Click the report.</span></span>

     <span data-ttu-id="2dcce-109">レポートが実行されます。</span><span class="sxs-lookup"><span data-stu-id="2dcce-109">The report runs.</span></span> <span data-ttu-id="2dcce-110">レポートがパラメーター化されている場合は、警告メッセージを受け取る目的に適ったデータがレポートに表示されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2dcce-110">If the report is parameterized, verify that the report shows the data that you want to receive alert messages about.</span></span> <span data-ttu-id="2dcce-111">目的の列または値が表示されない場合は、別のパラメーター値を使用してレポートを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dcce-111">If you do not see the columns or values you are interested in, you might want to rerun the report, using different parameter values.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="2dcce-112">レポートの実行用に選択したパラメーター値は、警告定義内に保存され、レポートが返される際に、警告定義の処理中のステップとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="2dcce-112">The parameter values you chose to run the report are saved in the alert definition and will be used when report is rerun as a step in processing the alert definition.</span></span> <span data-ttu-id="2dcce-113">異なるパラメーター値を使用するには、新しい警告定義を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dcce-113">To use different parameter values, you must create a new alert definition.</span></span>

3.  <span data-ttu-id="2dcce-114">**[アクション]** メニューの **[新しいデータの警告]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dcce-114">On the **Actions** menu, click **New Data Alert**.</span></span>

     <span data-ttu-id="2dcce-115">**[アクション]** メニューを次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="2dcce-115">The following picture shows the **Actions** menu.</span></span>

     <span data-ttu-id="2dcce-116">![SharePoint ライブラリから警告デザイナーを開く](media/rs-openalertdesigneriw.gif "SharePoint ライブラリから警告デザイナーを開く")</span><span class="sxs-lookup"><span data-stu-id="2dcce-116">![Open Alert Designer from SharePoint library](media/rs-openalertdesigneriw.gif "Open Alert Designer from SharePoint library")</span></span>

     <span data-ttu-id="2dcce-117">データ警告デザイナーが開き、レポートによって生成された最初のデータ フィードの先頭 100 行がテーブルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2dcce-117">The Data Alert Designer opens, showing the first 100 rows of the first data feed that the report generates in a table.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="2dcce-118">**[新しいデータの警告]** オプションが表示されない場合は、警告サービスが SharePoint サイト上に構成されていない、または [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディションにデータ警告が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="2dcce-118">If you do not see the **New Data Alert** option, the alerting service is not configured on the SharePoint site or the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] edition does not include data alerts.</span></span> <span data-ttu-id="2dcce-119">詳細については、「 [Reporting Services の SharePoint サービスとサービス アプリケーション](../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md)｣を参照してください</span><span class="sxs-lookup"><span data-stu-id="2dcce-119">For more information, see [Reporting Services SharePoint Service and Service Applications](../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md).</span></span>
    > 
    >  <span data-ttu-id="2dcce-120">**[新しいデータの警告]** オプションがグレーで表示されている場合は、レポート データ ソースが、統合セキュリティ資格情報を使用するか、または資格情報の入力を求めるように構成されています。</span><span class="sxs-lookup"><span data-stu-id="2dcce-120">If the **New Data Alert** option is grayed, the report data source is configured to use integrated security credentials or prompt for credentials.</span></span> <span data-ttu-id="2dcce-121">**[新しいデータの警告]** オプションを利用可能にするには、データ ソースを更新して、保存された資格情報を使用するようにするか、または資格情報を使用しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dcce-121">To make the **New Data Alert** option available, you must update the data source to use stored credentials or no credentials.</span></span>

     <span data-ttu-id="2dcce-122">データ フィードの名前は、 **[レポート データ名]** ボックスの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2dcce-122">The name of the data feed appears in **Report data name** drop-down list.</span></span>

4.  <span data-ttu-id="2dcce-123">必要に応じて、 **[レポート データ名]** ボックスの一覧から異なるデータ フィードを選択します。</span><span class="sxs-lookup"><span data-stu-id="2dcce-123">Optionally, select a different data feed in the **Report data name** drop-down list.</span></span>

     <span data-ttu-id="2dcce-124">レポートからデータ フィードが生成されない場合、そのレポートに対して警告定義を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="2dcce-124">If no data feed is generated from the report, you cannot create an alert definition for the report.</span></span> <span data-ttu-id="2dcce-125">各データ フィードの内容は、レポートのレイアウトによって決まります。</span><span class="sxs-lookup"><span data-stu-id="2dcce-125">The layout of the report determines the content of each data feed.</span></span> <span data-ttu-id="2dcce-126">詳細については、「[レポートからのデータフィードの生成 &#40;レポートビルダーと SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dcce-126">For more information see, [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).</span></span>

5.  <span data-ttu-id="2dcce-127">必要に応じて、 **[警告名]** ボックスに表示される既定の名前を、よりわかりやすい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="2dcce-127">Optionally, in the **Alert name** text box, update the default name to be more meaningful.</span></span>

     <span data-ttu-id="2dcce-128">レポートの名前が、警告定義の既定の名前として使用されます。</span><span class="sxs-lookup"><span data-stu-id="2dcce-128">The default name of the alert definition is the name of the report.</span></span> <span data-ttu-id="2dcce-129">警告定義名は必ずしも一意である必要はありませんが、後でデータ警告マネージャーで警告の一覧を表示したときに区別しづらくなる可能性はあります。</span><span class="sxs-lookup"><span data-stu-id="2dcce-129">Alert definition names do not have to be unique, which can make it difficult to tell them apart when you later view the list of your alerts in Data Alert Manager.</span></span> <span data-ttu-id="2dcce-130">警告定義には、一意でわかりやすい名前を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2dcce-130">It is recommended that you use meaningful and unique names for your alert definitions.</span></span>

6.  <span data-ttu-id="2dcce-131">必要に応じて、既定のデータ オプションを **[データ フィード内のいずれかのデータに次が含まれる]** から **[データ フィード内のどのデータにも次のものが含まれていません]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="2dcce-131">Optionally, change the default data option from **any data in the data feed has** to **no data in the data feed has**.</span></span>

7.  <span data-ttu-id="2dcce-132">[**ルールの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dcce-132">Click **Add rule**.</span></span>

     <span data-ttu-id="2dcce-133">データ フィード内の列の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2dcce-133">A list of the columns in the data feed appears.</span></span>

8.  <span data-ttu-id="2dcce-134">ルールに使用する列をリストから選択し、比較演算子を選択して、しきい値を入力します。</span><span class="sxs-lookup"><span data-stu-id="2dcce-134">In the list, select the column that you want to use in the rule, and then select a comparison operator and enter the threshold value.</span></span>

     <span data-ttu-id="2dcce-135">一覧表示される比較演算子は、選択した列のデータ型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="2dcce-135">Depending on the data type of the selected column, different comparison operators are listed.</span></span> <span data-ttu-id="2dcce-136">日付データ型の列の場合、ルールのしきい値の横にカレンダーのアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2dcce-136">If the column has a date data type, a calendar icon displays next to threshold value for the rule.</span></span> <span data-ttu-id="2dcce-137">カレンダーの日付をクリックするか日付を入力してデータを入力できます。</span><span class="sxs-lookup"><span data-stu-id="2dcce-137">You can enter a data by clicking a date in the calendar or typing the date.</span></span>

     <span data-ttu-id="2dcce-138">データ警告デザイナーでは、 **[値入力モード]** と **[フィールドの選択モード]** の 2 つの比較モードが提供されます。</span><span class="sxs-lookup"><span data-stu-id="2dcce-138">Data Alert Designer provides two comparison modes: **Value Entry Mode** and **Field Selection Mode**.</span></span> <span data-ttu-id="2dcce-139">既定のモードは **[値入力モード]** です。</span><span class="sxs-lookup"><span data-stu-id="2dcce-139">The default mode is **Value Entry Mode**.</span></span> <span data-ttu-id="2dcce-140">OR 句は、 **[値入力モード]** で **is** 比較を使用している場合にのみ追加できます。</span><span class="sxs-lookup"><span data-stu-id="2dcce-140">You can add OR clauses only when you are in **Value Entry Mode** and are using the **is** comparison.</span></span>

9. <span data-ttu-id="2dcce-141">OR 句を追加するには、下矢印をクリックし、 **[値入力モード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dcce-141">To add an OR clause, click the down-arrow, and then click **Value Entry Mode**.</span></span>

10. <span data-ttu-id="2dcce-142">比較値を入力します。</span><span class="sxs-lookup"><span data-stu-id="2dcce-142">Type the comparison value.</span></span>

11. <span data-ttu-id="2dcce-143">必要に応じて、省略記号ボタン ([. **..])** をもう一度クリックします。</span><span class="sxs-lookup"><span data-stu-id="2dcce-143">Optionally, click the ellipsis **(...)** again.</span></span>

     <span data-ttu-id="2dcce-144">省略記号 **(...)** は、最初の句が含まれている行に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2dcce-144">The ellipsis **(...)** appears on the line that contains the first clause.</span></span>

     <span data-ttu-id="2dcce-145">OR 句は、AND ルール内および下に追加されます。</span><span class="sxs-lookup"><span data-stu-id="2dcce-145">An OR clause is added below and within the AND rule.</span></span>

12. <span data-ttu-id="2dcce-146">必要に応じて、下矢印をクリックし、 **[フィールドの選択モード]** を選択して、一覧内の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="2dcce-146">Optionally, click the down-arrow, select **Field Selection Mode**, and then select a column in the list.</span></span>

     <span data-ttu-id="2dcce-147">または句を追加するためにクリックした省略記号 **(...)** が消えていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="2dcce-147">You will notice that the ellipsis **(...)** that you click to add OR clauses has disappeared.</span></span>

13. <span data-ttu-id="2dcce-148">必要に応じて、再度 **[ルールの追加]** をクリックし、ルールを追加します。</span><span class="sxs-lookup"><span data-stu-id="2dcce-148">Optionally, click **Add rule** again to add additional rules.</span></span>

     <span data-ttu-id="2dcce-149">ルールは AND 論理演算子を使用して組み合わされます。</span><span class="sxs-lookup"><span data-stu-id="2dcce-149">The rules are combined by using the AND logical operator.</span></span>

14. <span data-ttu-id="2dcce-150">定期的なパターンの一覧でオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="2dcce-150">Select an option in the recurrence list.</span></span> <span data-ttu-id="2dcce-151">定期的なパターンの種類に応じた間隔を入力してください。</span><span class="sxs-lookup"><span data-stu-id="2dcce-151">Depending on the type of recurrence, enter an interval.</span></span>

15. <span data-ttu-id="2dcce-152">必要に応じて、 **[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dcce-152">Optionally, click **Advanced**.</span></span>

16. <span data-ttu-id="2dcce-153">必要に応じて、警告メッセージの開始日付を変更します。異なる日付を入力するか、カレンダーを開いて目的の日付をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dcce-153">Optionally, change the date that the alert message starts on by typing a different date or opening the calendar, and then clicking a date in the calendar.</span></span>

     <span data-ttu-id="2dcce-154">現在の日付が既定の開始日になります。</span><span class="sxs-lookup"><span data-stu-id="2dcce-154">The default start date is the current date.</span></span>

17. <span data-ttu-id="2dcce-155">必要に応じて、 **[警告の停止日時]** の横にあるチェック ボックスをオンにし、警告メッセージを停止する日付を選択します。</span><span class="sxs-lookup"><span data-stu-id="2dcce-155">Optionally, select the checkbox located next to **Stop alert on**, and then choose a date to stop the alert message.</span></span>

     <span data-ttu-id="2dcce-156">既定では、警告メッセージに停止日はありません。</span><span class="sxs-lookup"><span data-stu-id="2dcce-156">By default, an alert message has no stop date.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="2dcce-157">通知メッセージを停止しても、警告定義は削除されません。</span><span class="sxs-lookup"><span data-stu-id="2dcce-157">Stopping an alert message does not delete the alert definition.</span></span> <span data-ttu-id="2dcce-158">停止した警告メッセージは、開始日と停止日を更新することで再度開始できます。</span><span class="sxs-lookup"><span data-stu-id="2dcce-158">After you stop an alert message, you can restart it by updating the start and stop dates.</span></span> <span data-ttu-id="2dcce-159">警告定義の削除の詳細については、「 [データ警告マネージャーでのデータ警告の管理](manage-my-data-alerts-in-data-alert-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dcce-159">For information about deleting alert definitions, see [Manage My Data Alerts in Data Alert Manager](manage-my-data-alerts-in-data-alert-manager.md).</span></span>

18. <span data-ttu-id="2dcce-160">必要に応じて、 **[結果が変更された場合にのみメッセージを送信]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="2dcce-160">Optionally, clear the **Send message only if results change** checkbox.</span></span>

     <span data-ttu-id="2dcce-161">警告メッセージを頻繁に送信する場合、冗長な情報は好ましくない可能性があるため、このチェック ボックスをオフにしないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2dcce-161">If you send alert messages frequently, redundant information might not be welcome and you should not clear this checkbox.</span></span>

19. <span data-ttu-id="2dcce-162">警告メッセージの受信者の電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="2dcce-162">Enter the email addresses of alert message recipients.</span></span> <span data-ttu-id="2dcce-163">複数のアドレスはセミコロンで区切って入力してください。</span><span class="sxs-lookup"><span data-stu-id="2dcce-163">Separate addresses with semicolons.</span></span>

     <span data-ttu-id="2dcce-164">警告定義の作成者の電子メール アドレスが利用できる場合は、 **[受信者]** ボックスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="2dcce-164">If the email address of the person who created the alert definition is available, it is added to the **Recipient(s)** box.</span></span>

20. <span data-ttu-id="2dcce-165">必要に応じて、 **[件名]** ボックスで、警告メッセージの件名行を更新します。</span><span class="sxs-lookup"><span data-stu-id="2dcce-165">Optionally, in the **Subject** text box, update the Subject line of the alert message.</span></span>

     <span data-ttu-id="2dcce-166">既定のサブジェクトは、 \*\* \<data alert name> のデータ警告\*\*です。</span><span class="sxs-lookup"><span data-stu-id="2dcce-166">The default Subject is **Data alert for \<data alert name>**.</span></span>

21. <span data-ttu-id="2dcce-167">必要に応じて、 **[説明]** ボックスに警告メッセージの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="2dcce-167">Optionally, in the **Description** text box, type a description of the alert message.</span></span>

22. <span data-ttu-id="2dcce-168">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dcce-168">Click **Save**.</span></span>

## <a name="see-also"></a><span data-ttu-id="2dcce-169">参照</span><span class="sxs-lookup"><span data-stu-id="2dcce-169">See Also</span></span>
 <span data-ttu-id="2dcce-170">データ警告[デザイナー](../../2014/reporting-services/data-alert-designer.md) [の警告管理者のデータ警告マネージャー](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) [Reporting Services データ警告](../ssms/agent/alerts.md)</span><span class="sxs-lookup"><span data-stu-id="2dcce-170">[Data Alert Designer](../../2014/reporting-services/data-alert-designer.md) [Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) [Reporting Services Data Alerts](../ssms/agent/alerts.md)</span></span>


