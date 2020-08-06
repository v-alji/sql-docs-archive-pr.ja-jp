---
title: '[オブジェクト エクスプローラーのシステム オブジェクトを非表示にする] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- hiding system objects
- system objects [SQL Server]
- objects [SQL Server], hiding
- Object Explorer, hiding objects
ms.assetid: c01d8804-838c-4f75-b78c-80e41e4fffdc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1e039446191154144dd6660fa6e8d3b4b65d1013
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630767"
---
# <a name="hide-system-objects-in-object-explorer"></a><span data-ttu-id="82684-102">[オブジェクト エクスプローラーのシステム オブジェクトを非表示にする]</span><span class="sxs-lookup"><span data-stu-id="82684-102">Hide System Objects in Object Explorer</span></span>
  <span data-ttu-id="82684-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、オブジェクト エクスプローラーのシステム オブジェクトを非表示にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="82684-103">This topic describes how to hide system objects in Object Explorer in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="82684-104">オブジェクト エクスプローラーの **[データベース]** ノードには、システム データベースなどのシステム オブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="82684-104">The **Databases** node of Object Explorer contains system objects such as the system databases.</span></span> <span data-ttu-id="82684-105">システム オブジェクトを非表示にするには、 **[ツール]** / **[オプション]** ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="82684-105">Use the **Tools**/**Options** pages to hide the system objects.</span></span> <span data-ttu-id="82684-106">システム関数やシステム データ型など、システム オブジェクトの中にはこの設定で非表示にならないものもあります。</span><span class="sxs-lookup"><span data-stu-id="82684-106">Some system objects, such as system functions and system data types, are not affected by this setting.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="82684-107">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="82684-107">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-hide-system-objects-in-object-explorer"></a><span data-ttu-id="82684-108">オブジェクト エクスプローラーでシステム オブジェクトを非表示にするには</span><span class="sxs-lookup"><span data-stu-id="82684-108">To hide system objects in Object Explorer</span></span>  
  
1.  <span data-ttu-id="82684-109">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="82684-109">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="82684-110">**[環境/スタートアップ]** ページで、 **[オブジェクト エクスプローラーのシステム オブジェクトを非表示にする]** を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="82684-110">On the **Environment/Startup** page, select **Hide system objects in Object Explorer**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="82684-111">この変更を有効にするには SQL Server Management Studio の再起動が必要であることを示すメッセージが表示されたら、 **[SQL Server Management Studio]** ダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="82684-111">In the **SQL Server Management Studio** dialog box, click **OK** to acknowledge that SQL Server Management Studio must be restarted for this change to take effect.</span></span>  
  
4.  <span data-ttu-id="82684-112">SQL Server Management Studio を閉じ、再度開きます。</span><span class="sxs-lookup"><span data-stu-id="82684-112">Close and reopen SQL Server Management Studio.</span></span>  
  
  
