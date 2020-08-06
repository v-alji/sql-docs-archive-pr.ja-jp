---
title: 'タスク 5: クレンジング結果を Excel ファイルにエクスポートする |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: eaeafd65-d0d4-4a7d-a3ad-110ef644e90b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0dbdc1bef348e03e211e4933132985ea2c089b97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643658"
---
# <a name="task-5-exporting-cleansing-results-to-an-excel-file"></a><span data-ttu-id="52688-102">タスク 5: Excel ファイルにクレンジングの結果をエクスポートする</span><span class="sxs-lookup"><span data-stu-id="52688-102">Task 5: Exporting Cleansing Results to an Excel File</span></span>
  <span data-ttu-id="52688-103">ここでは、クレンジング アクティビティから Excel ファイルに結果をエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="52688-103">In this task, you export results from the cleansing activity to an Excel file.</span></span> <span data-ttu-id="52688-104">詳細については、「[エクスポートステージ](https://msdn.microsoft.com/library/hh213061.aspx#Export)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52688-104">See [Export Stage](https://msdn.microsoft.com/library/hh213061.aspx#Export) topic for more details.</span></span>  
  
1.  <span data-ttu-id="52688-105">右ペインで、[**変換先の種類**] に [ **Excel** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="52688-105">In the right pane, select **Excel** for the **Destination Type**.</span></span>  
  
2.  <span data-ttu-id="52688-106">[**参照**] をクリックして、出力ファイル名をクレンジング済みの**Supplier List.xls**として指定し、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52688-106">Click **Browse**, specify the output file name as **Cleansed Supplier List.xls**, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="52688-107">クレンジングされたデータのみをエクスポートするには、**出力**形式に対して**のみデータ**を選択します。</span><span class="sxs-lookup"><span data-stu-id="52688-107">Select **Data Only** for the **Output** format to export just the cleansed data.</span></span> <span data-ttu-id="52688-108">2番目のオプションである [**データ] と [クレンジング情報**] を使用すると、クレンジングアクティビティの詳細とクレンジングされたデータをエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="52688-108">The second option, **Data and Cleansing Info**, lets you export cleansing activity details along with the cleansed data.</span></span> <span data-ttu-id="52688-109">[**形式の標準化**] オプションを使用すると、ドメインで定義したすべての出力形式を、そのドメインの値に適用できます。</span><span class="sxs-lookup"><span data-stu-id="52688-109">The **Standardize Format** option lets you apply any output formats you define on a domain to the values of that domain.</span></span> <span data-ttu-id="52688-110">チュートリアルのドメインには、出力形式を定義していません。</span><span class="sxs-lookup"><span data-stu-id="52688-110">You have not defined an output format on any domain in the tutorial.</span></span>  
  
     <span data-ttu-id="52688-111">![クレンジングの結果ページのエクスポート](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "クレンジングの結果ページのエクスポート")</span><span class="sxs-lookup"><span data-stu-id="52688-111">![Export Cleansing Results Page](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "Export Cleansing Results Page")</span></span>  
  
4.  <span data-ttu-id="52688-112">[**エクスポート**] をクリックしてデータをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="52688-112">Click **Export** to export the data.</span></span> <span data-ttu-id="52688-113">まだ [**完了**] をクリックしないでください。</span><span class="sxs-lookup"><span data-stu-id="52688-113">Do not click **Finish** yet.</span></span>  
  
5.  <span data-ttu-id="52688-114">[**エクスポート**中] ダイアログボックスで [**閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52688-114">Click **Close** on the **Exporting** dialog box.</span></span>  
  
6.  <span data-ttu-id="52688-115">[**完了**] をクリックして活動を終了します。</span><span class="sxs-lookup"><span data-stu-id="52688-115">Click **Finish** to finish the activity.</span></span> <span data-ttu-id="52688-116">[**完了**] をクリックする前に結果のエクスポートを忘れた場合は、 **DQS クライアント**のメインページで [**データ品質プロジェクトを開く**] をクリックし、プロジェクトの一覧から [**クレンジング Supplier list** ] を選択し、画面の下部にある [**次へ**] をクリックして、クレンジングプロセスの**エクスポート**ステージに移動します。</span><span class="sxs-lookup"><span data-stu-id="52688-116">If you forgot to export results before clicking **Finish**, click **Open Data Quality Project** in the main page of **DQS Client**, select **Cleanse Supplier List** from the list of projects, and click **Next** at the bottom of the screen to get to the **Export** stage of cleansing process again.</span></span> <span data-ttu-id="52688-117">[**戻る**] ボタンをクリックして **、[管理] と [結果の表示**] タブに切り替えることもできます。</span><span class="sxs-lookup"><span data-stu-id="52688-117">You can also switch to **Manage and View Results** tab by clicking **Back** button.</span></span>  
  
7.  <span data-ttu-id="52688-118">クレンジングされた**サプライヤー List.xls**を開き、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="52688-118">Open the **Cleansed Supplier List.xls** and do the following:</span></span>  
  
    1.  <span data-ttu-id="52688-119">ワークシートで adventure-work.com を検索することによって、末尾が "adventure-work.com" (文字が ' ではない) の電子メールアドレスがないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="52688-119">Ensure that there are no email addresses that end with adventure-work.com (without character 's') by searching for adventure-work.com in the worksheet.</span></span>  
  
    2.  <span data-ttu-id="52688-120">**Country**列に**USA**の値がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="52688-120">See that there is no **USA** value in the **Country** column.</span></span>  
  
    3.  <span data-ttu-id="52688-121">**ロサンゼルス**を検索し、**状態**が**CA**に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="52688-121">Search for **Los Angeles** and see that the **State** is set to **CA**.</span></span>  
  
    4.  <span data-ttu-id="52688-122">「 **Co.**」、「 **Corp.**」、および「 **inc.**」という用語がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="52688-122">Confirm that there are no terms **Co.**, **Corp.**, and **Inc.**.</span></span>  
  
    5.  <span data-ttu-id="52688-123">スプレッドシートから**Address Validation**列を削除し、excel ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="52688-123">Delete the **Address Validation** column from the spreadsheet and save the excel file.</span></span> <span data-ttu-id="52688-124">この追加列は Address Validation 複合ドメインに対応します。</span><span class="sxs-lookup"><span data-stu-id="52688-124">This additional column corresponds to the Address Validation composite domain.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="52688-125">次の手順</span><span class="sxs-lookup"><span data-stu-id="52688-125">Next Step</span></span>  
 [<span data-ttu-id="52688-126">タスク 6: Cleanse Supplier List プロジェクトから値をインポートする</span><span class="sxs-lookup"><span data-stu-id="52688-126">Task 6: Importing Values from the Cleanse Supplier List Project</span></span>](../../2014/tutorials/task-6-importing-values-from-the-cleanse-supplier-list-project.md)  
  
  
