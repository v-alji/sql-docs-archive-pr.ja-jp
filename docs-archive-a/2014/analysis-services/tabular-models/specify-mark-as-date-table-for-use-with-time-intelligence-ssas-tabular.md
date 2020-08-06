---
title: タイムインテリジェンスで使用する日付テーブルとしてマークを指定する (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 30841d1f-0c3b-4575-8f4a-27a1492e248c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 81038369b8cb8636a2aa216f1c26783a96d5f7ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711041"
---
# <a name="specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular"></a><span data-ttu-id="b4081-102">タイム インテリジェンスで使用する [日付テーブルとしてマーク] の指定 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="b4081-102">Specify Mark as Date Table for use with Time Intelligence (SSAS Tabular)</span></span>
  <span data-ttu-id="b4081-103">DAX 数式のタイム インテリジェンス機能を使用するには、日付テーブルと Date データ型の一意の識別子 (datetime) の列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4081-103">In order to use time intelligence functions in DAX formulas, you must specify a date table and a unique identifier (datetime) column of the Date data type.</span></span> <span data-ttu-id="b4081-104">日付テーブルの列が一意の識別子として指定されている場合は、日付テーブル内の列と任意のファクト テーブルのリレーションシップを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b4081-104">Once a column in the date table is specified as a unique identifier, you can create relationships between columns in the date table and any fact tables.</span></span>  
  
 <span data-ttu-id="b4081-105">タイム インテリジェンス機能を使用する場合、次のルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="b4081-105">When using time intelligence functions, the following rules apply:</span></span>  
  
-   <span data-ttu-id="b4081-106">DAX タイム インテリジェンス機能を使用する場合は、ファクト テーブルから datetime 列を指定しない。</span><span class="sxs-lookup"><span data-stu-id="b4081-106">When using DAX time intelligence functions, never specify a datetime column from a fact table.</span></span> <span data-ttu-id="b4081-107">1 つ以上の datetime 列 (Date データ型で、一意の値を持つ) を含む独立した日付テーブルをモデル内に必ず作成する。</span><span class="sxs-lookup"><span data-stu-id="b4081-107">Always create a separate date table in your model with at least one datetime column of Date data type and with unique values.</span></span>  
  
-   <span data-ttu-id="b4081-108">日付テーブルの日付の範囲が連続している。</span><span class="sxs-lookup"><span data-stu-id="b4081-108">Make sure your date table has a continuous date range.</span></span>  
  
-   <span data-ttu-id="b4081-109">日付テーブル内の datetime 列の粒度は日単位 (1 日未満の時間を含まない) にする。</span><span class="sxs-lookup"><span data-stu-id="b4081-109">The datetime column in the date table should be at day granularity (without fractions of a day).</span></span>  
  
-   <span data-ttu-id="b4081-110">**[日付テーブルとしてマーク]** ダイアログ ボックスを使用して、日付テーブルと一意識別子列を指定する必要がある。</span><span class="sxs-lookup"><span data-stu-id="b4081-110">You must specify a date table and a unique identifier column by using the **Mark the Date Table** dialog box.</span></span>  
  
-   <span data-ttu-id="b4081-111">日付テーブル内の Date データ型の列とファクト テーブルの間にリレーションシップを作成する。</span><span class="sxs-lookup"><span data-stu-id="b4081-111">Create relationships between fact tables and columns of Date data type in the date table.</span></span>  
  
#### <a name="to-specify-a-date-table-and-unique-identifier"></a><span data-ttu-id="b4081-112">日付テーブルと一意識別子を指定するには</span><span class="sxs-lookup"><span data-stu-id="b4081-112">To specify a date table and unique identifier</span></span>  
  
1.  <span data-ttu-id="b4081-113">モデル デザイナーで、日付テーブルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b4081-113">In the model designer, click the date table.</span></span>  
  
2.  <span data-ttu-id="b4081-114">**[テーブル]** メニュー、 **[日付]**、 **Mark as [日付] [テーブル]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="b4081-114">Click the **Table** menu, then click **Date**, and then click **Mark as Date Table**</span></span>  
  
3.  <span data-ttu-id="b4081-115">**[日付テーブルとしてマーク]** ダイアログ ボックスの **[日付]** ボックスの一覧で、一意識別子として使用する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="b4081-115">In the **Mark as Date Table** dialog box, in the **Date** listbox, select a column to be used as a unique identifier.</span></span> <span data-ttu-id="b4081-116">この列は、一意の値を含んでいる必要があり、Date データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4081-116">This column must contain unique values and should be of Date data type.</span></span> <span data-ttu-id="b4081-117">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b4081-117">For example:</span></span>  
  
    |<span data-ttu-id="b4081-118">Date</span><span class="sxs-lookup"><span data-stu-id="b4081-118">Date</span></span>|  
    |----------|  
    |<span data-ttu-id="b4081-119">7/1/2010 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="b4081-119">7/1/2010 12:00:00 AM</span></span>|  
    |<span data-ttu-id="b4081-120">7/2/2010 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="b4081-120">7/2/2010 12:00:00 AM</span></span>|  
    |<span data-ttu-id="b4081-121">7/3/2010 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="b4081-121">7/3/2010 12:00:00 AM</span></span>|  
    |<span data-ttu-id="b4081-122">7/4/2010 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="b4081-122">7/4/2010 12:00:00 AM</span></span>|  
    |<span data-ttu-id="b4081-123">7/5/2010 12:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="b4081-123">7/5/2010 12:00:00 AM</span></span>|  
  
4.  <span data-ttu-id="b4081-124">必要に応じて、ファクト テーブルと日付テーブルの間のリレーションシップを作成します。</span><span class="sxs-lookup"><span data-stu-id="b4081-124">If necessary, create any relationships between fact tables and the date table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4081-125">参照</span><span class="sxs-lookup"><span data-stu-id="b4081-125">See Also</span></span>  
 <span data-ttu-id="b4081-126">[SSAS 表形式&#41;&#40;計算](calculations-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="b4081-126">[Calculations &#40;SSAS Tabular&#41;](calculations-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="b4081-127">タイムインテリジェンス関数 &#40;DAX&#41;</span><span class="sxs-lookup"><span data-stu-id="b4081-127">Time Intelligence Functions &#40;DAX&#41;</span></span>](/dax/time-intelligence-functions-dax)  
  
  
