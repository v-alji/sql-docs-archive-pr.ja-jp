---
title: オンラインモードでの Analysis Services データベースへの接続 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, connecting
ms.assetid: 33041234-7106-404f-a289-8e904f32aff2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 363beb7132eae92907198979fe2d9892c5d07b79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737104"
---
# <a name="connect-in-online-mode-to-an-analysis-services-database"></a><span data-ttu-id="330de-102">Analysis Services データベースへのオンライン モードでの接続</span><span class="sxs-lookup"><span data-stu-id="330de-102">Connect in Online Mode to an Analysis Services Database</span></span>
  <span data-ttu-id="330de-103">既存のデータベースに直接接続 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] し、そのデータベース内のオブジェクトを直接変更できます。</span><span class="sxs-lookup"><span data-stu-id="330de-103">You can connect directly to an existing [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database and directly modify objects within that database.</span></span> <span data-ttu-id="330de-104">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに直接接続すると、オブジェクトに対する変更処理が直ちに行われ、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトは [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]内に作成されません。</span><span class="sxs-lookup"><span data-stu-id="330de-104">When you connect directly to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, changes to objects occur immediately and no [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project is created within [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="to-connect-directly-to-an-analysis-services-database-by-using-sql-server-data-tools"></a><span data-ttu-id="330de-105">SQL Server データ ツールを使用して Analysis Services データベースに直接接続するには</span><span class="sxs-lookup"><span data-stu-id="330de-105">To Connect Directly to an Analysis Services Database by using SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="330de-106">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="330de-106">Open [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="330de-107">**[ファイル]** メニューの **[開く]** をポイントし、 **[Analysis Services データベース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="330de-107">On the **File** menu, point to **Open** and then click **Analysis Services Database**.</span></span>  
  
3.  <span data-ttu-id="330de-108">**[既存のデータベースに接続する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="330de-108">Select **Connect to existing database**.</span></span>  
  
4.  <span data-ttu-id="330de-109">サーバー名とデータベース名を指定します。</span><span class="sxs-lookup"><span data-stu-id="330de-109">Specify the server name and the database name.</span></span>  
  
     <span data-ttu-id="330de-110">データベース名は直接入力することも、サーバーをクエリして、サーバー上の既存のデータベースを表示してから選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="330de-110">You can either type the database name or query the server to view the existing databases on the server.</span></span>  
  
5.  <span data-ttu-id="330de-111">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="330de-111">Click **OK**.</span></span>  
  
     <span data-ttu-id="330de-112">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース内のオブジェクトを直接編集できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="330de-112">You can now directly edit any objects within the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="330de-113">参照</span><span class="sxs-lookup"><span data-stu-id="330de-113">See Also</span></span>  
 <span data-ttu-id="330de-114">[開発段階での Analysis Services プロジェクトとデータベースの操作](work-with-analysis-services-projects-and-databases-in-development.md) </span><span class="sxs-lookup"><span data-stu-id="330de-114">[Working with Analysis Services Projects and Databases During the Development Phase](work-with-analysis-services-projects-and-databases-in-development.md) </span></span>  
 [<span data-ttu-id="330de-115">SQL Server データ ツール &#40;SSDT&#41; を使用した多次元モデルの作成</span><span class="sxs-lookup"><span data-stu-id="330de-115">Creating Multidimensional Models Using SQL Server Data Tools &#40;SSDT&#41;</span></span>](creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)  
  
  
