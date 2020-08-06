---
title: 'タスク 4: 照合アクティビティから Excel ファイルに結果をエクスポートする |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 644454c4-3c5a-469a-90ec-e51dc7fb99fc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b583e44f887fc0595fb904ec977f1de28c2fecd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720415"
---
# <a name="task-4-exporting-the-results-from-matching-activity-to-an-excel-file"></a><span data-ttu-id="a7d37-102">タスク 4: 照合アクティビティから Excel ファイルに結果をエクスポートする</span><span class="sxs-lookup"><span data-stu-id="a7d37-102">Task 4: Exporting the Results from Matching Activity to an Excel File</span></span>
  <span data-ttu-id="a7d37-103">ここでは、照合アクティビティから Excel ファイルに結果をエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="a7d37-103">In this task, you export the results from the matching activity to an Excel file.</span></span>

1.  <span data-ttu-id="a7d37-104">[**エクスポート**] ページで、**変換先の種類**として [ **Excel ファイル**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a7d37-104">In the **Export** page, select **Excel File** for the **Destination Type**.</span></span>

2.  <span data-ttu-id="a7d37-105">**サバイバーシップ Results**オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="a7d37-105">Select **Survivorship Results** option.</span></span> <span data-ttu-id="a7d37-106">サバイバーシッププロセスでは、選択した**サバイバーシップルール**に基づいて、各クラスターの保持レコードが DQS によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="a7d37-106">In the survivorship process, DQS determines a survivor record for each cluster based on the **Survivorship Rule** you selected.</span></span>

3.  <span data-ttu-id="a7d37-107">[**参照**] をクリックし、出力ファイルを保存するフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="a7d37-107">Click **Browse** and navigate to the folder where you want to store the output file.</span></span>

4.  <span data-ttu-id="a7d37-108">名前として「**クレンジングして一致**した Suppliers.xls」と入力し、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7d37-108">Type **Cleansed and Matched Suppliers.xls** for the name and click **Open**.</span></span>

5.  <span data-ttu-id="a7d37-109">**サバイバーシップルール**に [**ピボットレコード**が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a7d37-109">Confirm that **Pivot Record** is selected for the **Survivorship Rule**.</span></span> <span data-ttu-id="a7d37-110">このオプションを選択すると、各クラスターのピボット レコードがクラスターからの出力に選択されます。</span><span class="sxs-lookup"><span data-stu-id="a7d37-110">When you select this option, the pivot record for each cluster is picked for the output from a cluster.</span></span> <span data-ttu-id="a7d37-111">サバイバーシップ ルールの他のオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a7d37-111">The other options for the Survivorship Rule are:</span></span>

    1.  <span data-ttu-id="a7d37-112">**最も完全なレコード:** 保持 record は、入力されたフィールドの数が最も多いレコードです。</span><span class="sxs-lookup"><span data-stu-id="a7d37-112">**Most complete record:** Survivor record is the one with the largest number of populated fields.</span></span>

    2.  <span data-ttu-id="a7d37-113">**最長のレコード:** 保持 record は、ソースフィールド内の用語の数が最も多いレコードです。</span><span class="sxs-lookup"><span data-stu-id="a7d37-113">**Longest record:** Survivor record is the one with the largest number of terms in source fields.</span></span>

    3.  <span data-ttu-id="a7d37-114">**最も完全で最長のレコード:** 保持 record は、入力されたフィールドの数が最も多く、各フィールドに含まれる用語の数が最も多いレコードです。</span><span class="sxs-lookup"><span data-stu-id="a7d37-114">**Most complete and longest record:** Survivor record is the one with the largest number of populated fields, and has the largest number of terms in each field.</span></span>

     <span data-ttu-id="a7d37-115">![照合の結果ページのエクスポート](../../2014/tutorials/media/et-exportingtheresultsfrommatoanexcelfile.jpg "照合の結果ページのエクスポート")</span><span class="sxs-lookup"><span data-stu-id="a7d37-115">![Export Results from Matching Page](../../2014/tutorials/media/et-exportingtheresultsfrommatoanexcelfile.jpg "Export Results from Matching Page")</span></span>

6.  <span data-ttu-id="a7d37-116">[**エクスポート**] をクリックして、結果を Excel ファイルにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="a7d37-116">Click **Export** to export the results to an Excel file.</span></span>

7.  <span data-ttu-id="a7d37-117">[**閉じる**] をクリックして、[**一致するエクスポート**] ダイアログボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a7d37-117">Click **Close** to close the **Matching Export** dialog box.</span></span>

8.  <span data-ttu-id="a7d37-118">[**完了**] をクリックして照合アクティビティを終了します。</span><span class="sxs-lookup"><span data-stu-id="a7d37-118">Click **Finish** to finish the matching activity.</span></span>

9. <span data-ttu-id="a7d37-119">クレンジングされて一致した**Suppliers.xlsx**ファイルを開き、重複がないことを確認します ([仕入先])。</span><span class="sxs-lookup"><span data-stu-id="a7d37-119">Open the **Cleansed and Matched Suppliers.xlsx** file and confirm that you do not see any duplicates (SupplierID).</span></span>

 <span data-ttu-id="a7d37-120">これで、仕入先データは重複項目を削除するためにクレンジングおよび照合されました。</span><span class="sxs-lookup"><span data-stu-id="a7d37-120">Now, you have supplier data that has been cleansed and matched to remove duplicates.</span></span>

## <a name="next-step"></a><span data-ttu-id="a7d37-121">次の手順</span><span class="sxs-lookup"><span data-stu-id="a7d37-121">Next Step</span></span>
 [<span data-ttu-id="a7d37-122">レッスン 4: MDS に仕入先データを格納する</span><span class="sxs-lookup"><span data-stu-id="a7d37-122">Lesson 4: Storing Supplier Data in MDS</span></span>](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)


