---
title: ファイルの最大アップロードサイズの構成 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ac516c63-1e79-4ae8-bca6-32d3c1a09c00
author: minewiskan
ms.author: owend
ms.openlocfilehash: 34a0adb2f22915289cccfa1f21c51038263acca0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711058"
---
# <a name="configure-maximum-file-upload-size-powerpivot-for-sharepoint"></a><span data-ttu-id="fda97-102">アップロードするファイルの最大サイズの構成 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="fda97-102">Configure Maximum File Upload Size (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="fda97-103">PowerPivot ブックには大量のデータが含まれる場合が多く、SharePoint のアップロードで許容されるファイルの最大サイズを超過することがあります。</span><span class="sxs-lookup"><span data-stu-id="fda97-103">PowerPivot workbooks often contain large amounts of data that result in files that exceed the maximum file size allowed for SharePoint uploads.</span></span> <span data-ttu-id="fda97-104">最大サイズを超過したファイルをアップロードしようとすると、SharePoint で次のエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="fda97-104">When you try to upload a file that exceeds the upper limit, you will get the following error on SharePoint:</span></span>  
  
-   <span data-ttu-id="fda97-105">"指定されたファイルは、サポートされる最大ファイル サイズを超えています。"</span><span class="sxs-lookup"><span data-stu-id="fda97-105">"The specified file is larger than the maximum supported file size."</span></span>  
  
 <span data-ttu-id="fda97-106">ファイル サイズを増やすには、まず、Excel Services の [ブックの最大サイズ] を 50 MB に調整します。</span><span class="sxs-lookup"><span data-stu-id="fda97-106">To increase the file size, start by adjusting the Maximum Workbook Size for Excel Services to 50 megabytes.</span></span> <span data-ttu-id="fda97-107">これにより、Excel に対するファイルの最大サイズの上限が SharePoint Web アプリケーションに対するファイル サイズの上限 (SharePoint 2010 では既定で 50 MB、SharePoint 2013 では既定で 200 MB) と同じになります。</span><span class="sxs-lookup"><span data-stu-id="fda97-107">This aligns the maximum file size limits for Excel to those of SharePoint web applications (set to 50 megabytes by default in SharePoint 2010 and 200 in SharePoint 2013).</span></span> <span data-ttu-id="fda97-108">ファイルのサイズが 50 MB を超える場合は、Excel Services と Web アプリケーションの両方についてファイル サイズの上限を増やします。</span><span class="sxs-lookup"><span data-stu-id="fda97-108">If your files exceed 50 megabytes in size, increase the file size limits for both Excel Services and your web application.</span></span>  
  
 <span data-ttu-id="fda97-109">ファイルの最大アップロード サイズを変更するには、SharePoint 管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="fda97-109">You must be a SharePoint administrator to change the maximum file upload size.</span></span>  
  
### <a name="configure-maximum-file-size-for-excel-services"></a><span data-ttu-id="fda97-110">Excel Services に対するファイルの最大サイズの構成</span><span class="sxs-lookup"><span data-stu-id="fda97-110">Configure maximum file size for Excel Services</span></span>  
  
1.  <span data-ttu-id="fda97-111">サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda97-111">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="fda97-112">Excel Services アプリケーションの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda97-112">Click the name of your Excel Services Application.</span></span>  
  
3.  <span data-ttu-id="fda97-113">**[信頼できるファイル保存場所]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda97-113">Click **Trusted File Locations**.</span></span>  
  
4.  <span data-ttu-id="fda97-114">プロパティを編集する場所をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda97-114">Click the location to edit the properties.</span></span> <span data-ttu-id="fda97-115">既定では、既定の Web アプリケーションは信頼できるサイトと見なされます。</span><span class="sxs-lookup"><span data-stu-id="fda97-115">By default, Excel Services considers the default web application a trusted site.</span></span> <span data-ttu-id="fda97-116">既定の Web アプリケーションを使用している場合は、 **http://** をクリックして、この場所の構成ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="fda97-116">If you are using the default web application, click **http://** to open the configuration page for this location.</span></span>  
  
5.  <span data-ttu-id="fda97-117">**[ブックのプロパティ]** までスクロールします。</span><span class="sxs-lookup"><span data-stu-id="fda97-117">Scroll to **Workbook Properties**.</span></span>  
  
6.  <span data-ttu-id="fda97-118">[ブックの最大サイズ] で、ファイル サイズを 10 (既定値) から 50、または使用するファイルに対応できるさらに大きい値に増やします。</span><span class="sxs-lookup"><span data-stu-id="fda97-118">In Maximum Workbook Size, increase the file size from 10 (the default value) to 50 or a larger size that accommodates the files you are working with.</span></span>  
  
     <span data-ttu-id="fda97-119">既定では、50 MB が SharePoint Web アプリケーションのファイルの最大アップロード サイズです。</span><span class="sxs-lookup"><span data-stu-id="fda97-119">By default, 50 megabytes is the maximum file upload size for SharePoint web applications.</span></span> <span data-ttu-id="fda97-120">[ブックの最大サイズ] を 50 MB よりも大きい値に設定した場合は、次の手順に従って、SharePoint Web アプリケーションの [アップロードの最大サイズ] を同じ値に増やしてください。</span><span class="sxs-lookup"><span data-stu-id="fda97-120">If you set Maximum Workbook Size to a number larger than 50 megabytes, follow the steps in the next procedure to increase the Maximum Upload Size for your SharePoint web application to the same value.</span></span>  
  
     <span data-ttu-id="fda97-121">指定できる最大値は 2 GB (またはサーバーの全体管理で指定された 2047 MB) です。</span><span class="sxs-lookup"><span data-stu-id="fda97-121">The maximum value that you can specify is 2 gigabytes (or 2047 megabytes as specified in Central Administration).</span></span>  
  
7.  <span data-ttu-id="fda97-122">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda97-122">Click **OK**.</span></span>  
  
### <a name="configure-maximum-file-size-for-a-sharepoint-web-application"></a><span data-ttu-id="fda97-123">SharePoint Web アプリケーションに対するファイルの最大サイズの構成</span><span class="sxs-lookup"><span data-stu-id="fda97-123">Configure maximum file size for a SharePoint web application</span></span>  
  
1.  <span data-ttu-id="fda97-124">サーバーの全体管理で、[アプリケーション管理] の [ **web アプリケーションの管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda97-124">In Central Administration, in Application Management, click **Manage web applications**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fda97-125">以下の手順は、Excel Services の [ブックの最大サイズ] を大きい値に設定した場合にのみ実行してください。</span><span class="sxs-lookup"><span data-stu-id="fda97-125">Perform the following steps only if you increased the Maximum Workbook Size in Excel Services.</span></span>  
  
2.  <span data-ttu-id="fda97-126">アプリケーションを選択します ( **SharePoint -80**など)。</span><span class="sxs-lookup"><span data-stu-id="fda97-126">Select the application (for example, **SharePoint - 80**).</span></span>  
  
3.  <span data-ttu-id="fda97-127">[Web アプリケーション] リボンで、[全般設定] ボタンの下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda97-127">On the Web Applications ribbon, click the down arrow on the General Settings button.</span></span>  
  
4.  <span data-ttu-id="fda97-128">[**全般設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda97-128">Click **General Settings**.</span></span>  
  
5.  <span data-ttu-id="fda97-129">**[アップロードの最大サイズ]** までスクロールします。</span><span class="sxs-lookup"><span data-stu-id="fda97-129">Scroll to **Maximum Upload Size**.</span></span>  
  
6.  <span data-ttu-id="fda97-130">Excel Services の [ブックの最大サイズ] 以上の値にプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="fda97-130">Set the property to the same number, or larger as the Maximum Workbook Size in Excel Services.</span></span>  
  
7.  <span data-ttu-id="fda97-131">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fda97-131">Click **OK**.</span></span>  
  
  
