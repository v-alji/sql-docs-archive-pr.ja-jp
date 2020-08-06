---
title: 'タスク 2: DQS ドメインに Excel 列をマップする |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f347cc92-950f-4021-b7af-393640dfe821
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 293b035ff52845959e2c8b70c63df643ae6e3e55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644250"
---
# <a name="task-2-mapping-excel-columns-to-dqs-domains"></a><span data-ttu-id="11b34-102">タスク 2: DQS ドメインに Excel 列をマップする</span><span class="sxs-lookup"><span data-stu-id="11b34-102">Task 2: Mapping Excel Columns to DQS Domains</span></span>
    
1.  <span data-ttu-id="11b34-103">**[マップ]** ページの **[データ ソース]** で **[Excel ファイル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="11b34-103">In the **Map** page, select **Excel File** for **Data Source**.</span></span>  
  
2.  <span data-ttu-id="11b34-104">[**参照**] をクリックし、[ **Suppliers.xlsx**] を選択して、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11b34-104">Click **Browse**, select **Suppliers.xlsx**, and click **Open**.</span></span>  
  
3.  <span data-ttu-id="11b34-105">**ワークシート**の [ **IncomingSuppliers $** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="11b34-105">Select **IncomingSuppliers$** for the **Worksheet**.</span></span>  
  
4.  <span data-ttu-id="11b34-106">次の表とスクリーン ショットのように列をマップします。</span><span class="sxs-lookup"><span data-stu-id="11b34-106">Map columns as shown in the following table and screenshot.</span></span> <span data-ttu-id="11b34-107">**状態**ドメインのマッピングを作成する場合は、一覧のすぐ上にあるツールバーの [**列マッピングの追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="11b34-107">When creating mappings for the **State** domain, click **Add a column mapping** button on the toolbar located just above the list.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="11b34-108">クレンジングに**SUPPLIER ID**列またはドメインを使用していません。</span><span class="sxs-lookup"><span data-stu-id="11b34-108">You are not using **Supplier ID** column/domain for cleansing.</span></span> <span data-ttu-id="11b34-109">この照合アクティビティでは、後で**SUPPLIER ID**ドメインを使用します。</span><span class="sxs-lookup"><span data-stu-id="11b34-109">You will use the **Supplier ID** domain later in the matching activity.</span></span>  
  
    |<span data-ttu-id="11b34-110">Excel 列</span><span class="sxs-lookup"><span data-stu-id="11b34-110">Excel column</span></span>|<span data-ttu-id="11b34-111">DQS ドメイン</span><span class="sxs-lookup"><span data-stu-id="11b34-111">DQS Domain</span></span>|  
    |------------------|----------------|  
    |<span data-ttu-id="11b34-112">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="11b34-112">Supplier Name</span></span>|<span data-ttu-id="11b34-113">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="11b34-113">Supplier Name</span></span>|  
    |<span data-ttu-id="11b34-114">ContactEmailAddress</span><span class="sxs-lookup"><span data-stu-id="11b34-114">ContactEmailAddress</span></span>|<span data-ttu-id="11b34-115">連絡先のメール アドレス</span><span class="sxs-lookup"><span data-stu-id="11b34-115">Contact Email</span></span>|  
    |<span data-ttu-id="11b34-116">Address Line</span><span class="sxs-lookup"><span data-stu-id="11b34-116">Address Line</span></span>|<span data-ttu-id="11b34-117">Address Line</span><span class="sxs-lookup"><span data-stu-id="11b34-117">Address Line</span></span>|  
    |<span data-ttu-id="11b34-118">City</span><span class="sxs-lookup"><span data-stu-id="11b34-118">City</span></span>|<span data-ttu-id="11b34-119">City</span><span class="sxs-lookup"><span data-stu-id="11b34-119">City</span></span>|  
    |<span data-ttu-id="11b34-120">State</span><span class="sxs-lookup"><span data-stu-id="11b34-120">State</span></span>|<span data-ttu-id="11b34-121">State</span><span class="sxs-lookup"><span data-stu-id="11b34-121">State</span></span>|  
    |<span data-ttu-id="11b34-122">国 ([ **+ (列マッピングの追加)** ] ツールバーをクリックして行を追加します)</span><span class="sxs-lookup"><span data-stu-id="11b34-122">Country (Click **+(Add a column mapping)** toolbar to add a row)</span></span>|<span data-ttu-id="11b34-123">国</span><span class="sxs-lookup"><span data-stu-id="11b34-123">Country</span></span>|  
    |<span data-ttu-id="11b34-124">Zip Code</span><span class="sxs-lookup"><span data-stu-id="11b34-124">Zip Code</span></span>|<span data-ttu-id="11b34-125">Zip</span><span class="sxs-lookup"><span data-stu-id="11b34-125">Zip</span></span>|  
  
     <span data-ttu-id="11b34-126">![ドメインへの Excel 列のマッピング](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-01.jpg "ドメインへの Excel 列のマッピング")</span><span class="sxs-lookup"><span data-stu-id="11b34-126">![Mappings of Excel Columns to Domains](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-01.jpg "Mappings of Excel Columns to Domains")</span></span>  
  
5.  <span data-ttu-id="11b34-127">**Address Validation**複合ドメイン内の個々のドメインをすべてマップしているため、複合ドメインは自動的にクレンジングプロセスに参加します。</span><span class="sxs-lookup"><span data-stu-id="11b34-127">As you have mapped all the individual domains within the **Address Validation** composite domain, the composite domain automatically participates in the cleansing process.</span></span> <span data-ttu-id="11b34-128">[**複合ドメインの表示と選択**] ボタンをクリックして、 **Address Validation**複合ドメインが自動的に選択されていることを確認し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11b34-128">Click **View/Select Composite Domains** button to see that the **Address Validation** composite domain is automatically selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="11b34-129">![[複合ドメインの表示と選択] ダイアログ ボックス](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-02.jpg "[複合ドメインの表示と選択] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="11b34-129">![View/Select Composite Domains Dialog Box](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-02.jpg "View/Select Composite Domains Dialog Box")</span></span>  
  
6.  <span data-ttu-id="11b34-130">[**次へ**] をクリックして、[**クレンジング**] ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="11b34-130">Click **Next** to switch to the **Cleanse** page.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="11b34-131">次の手順</span><span class="sxs-lookup"><span data-stu-id="11b34-131">Next Step</span></span>  
 [<span data-ttu-id="11b34-132">タスク 3: Suppliers ナレッジ ベースに対してデータをクレンジングする</span><span class="sxs-lookup"><span data-stu-id="11b34-132">Task 3: Cleansing Data against the Suppliers Knowledge Base</span></span>](../../2014/tutorials/task-3-cleansing-data-against-the-suppliers-knowledge-base.md)  
  
  
