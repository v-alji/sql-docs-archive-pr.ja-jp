---
title: オブジェクト エクスプローラー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.objectexplorer.commandsoptions
- SQL12.SWB.SQLSERVEROBJECTEXPLORER.DHELP
- sql12.swb.objectexplorer.scriptingoptions
- sql12.swb.oe.f1
helpviewer_keywords:
- multi-select [SQL Server Management Studio]
- Registered Servers [SQL Server], Object Explorer
- Query Editor [SQL Server Management Studio], Object Explorer
- connections [SQL Server], SQL Server Management Studio
- servers [SQL Server], Registered Servers
- Object Explorer
- SQL Server Management Studio [SQL Server], connections
- viewing objects
- filtering objects [SQL Server]
- Object Explorer, about Object Explorer
ms.assetid: 469ea8e2-79b9-44c8-bb6f-f0e1c5dbf0f2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3acefcd03af1b39d467625800d8837553ff5253b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641403"
---
# <a name="object-explorer"></a><span data-ttu-id="da756-102">オブジェクト エクスプローラー</span><span class="sxs-lookup"><span data-stu-id="da756-102">Object Explorer</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="da756-103">には、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]のインスタンス内のオブジェクトを管理するための機能が備わっています。</span><span class="sxs-lookup"><span data-stu-id="da756-103">provides features for managing objects in instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="benefits-of-object-explorer"></a><span data-ttu-id="da756-104">オブジェクト エクスプローラーの利点</span><span class="sxs-lookup"><span data-stu-id="da756-104">Benefits of Object Explorer</span></span>  
 <span data-ttu-id="da756-105">オブジェクト エクスプローラーは、SQL Server の各インスタンスのオブジェクトを表示し、管理するための階層形式のユーザー インターフェイスを備えています。</span><span class="sxs-lookup"><span data-stu-id="da756-105">Object Explorer provides a hierarchical user interface to view and manage the objects in each instance of SQL Server.</span></span> <span data-ttu-id="da756-106">[オブジェクト エクスプローラーの詳細] ペインには、インスタンス オブジェクトの表形式のビューと、特定のオブジェクトを検索する機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="da756-106">The Object Explorer Details pane presents a tabular view of instance objects, and the capability to search for specific objects.</span></span> <span data-ttu-id="da756-107">オブジェクト エクスプローラーの機能は、サーバーの種類によって多少異なりますが、データベースの開発機能と管理機能は、基本的にサーバーの種類にかかわりなく用意されています。</span><span class="sxs-lookup"><span data-stu-id="da756-107">The capabilities of Object Explorer vary slightly depending on the type of server, but generally include the development features for databases, and management features for all server types.</span></span>  
  
## <a name="object-explorer-tasks"></a><span data-ttu-id="da756-108">オブジェクト エクスプローラーのタスク</span><span class="sxs-lookup"><span data-stu-id="da756-108">Object Explorer Tasks</span></span>  
  
|<span data-ttu-id="da756-109">説明</span><span class="sxs-lookup"><span data-stu-id="da756-109">Description</span></span>|<span data-ttu-id="da756-110">トピック</span><span class="sxs-lookup"><span data-stu-id="da756-110">Topic</span></span>|  
|-----------------|-----------|  
|<span data-ttu-id="da756-111">オブジェクト エクスプローラーを開いて、その動作を定義するオプションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="da756-111">Describes how to open the Object Explorer and configure the options that define the behavior of the explorer.</span></span>|[<span data-ttu-id="da756-112">オブジェクト エクスプローラーを開き、構成する</span><span class="sxs-lookup"><span data-stu-id="da756-112">Open and Configure Object Explorer</span></span>](open-and-configure-object-explorer.md)|  
|<span data-ttu-id="da756-113">[!INCLUDE[ssDE](../../includes/ssde-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、および [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]のインスタンスにオブジェクト エクスプローラーを接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="da756-113">Describes how to connect Object Explorer to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>|[<span data-ttu-id="da756-114">オブジェクト エクスプローラーからインスタンスへの接続</span><span class="sxs-lookup"><span data-stu-id="da756-114">Connect to an Instance From Object Explorer</span></span>](connect-to-an-instance-from-object-explorer.md)|  
|<span data-ttu-id="da756-115">オブジェクト エクスプローラーの階層内のノードとして表されるオブジェクトを管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="da756-115">Describes how to manage objects represented as nodes in the Object Explorer hierarchy.</span></span>|[<span data-ttu-id="da756-116">オブジェクト エクスプローラーを使用したオブジェクトの管理</span><span class="sxs-lookup"><span data-stu-id="da756-116">Manage Objects by Using Object Explorer</span></span>](manage-objects-by-using-object-explorer.md)|  
|<span data-ttu-id="da756-117">サーバーのすべてのオブジェクトを表形式で表示し、それらを管理するためのユーザー インターフェイスを備えた [オブジェクト エクスプローラーの詳細] ペインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="da756-117">Describes the Object Explorer Details Pane, a tabular view of all of the objects in the server with a user interface to manage them.</span></span>|<span data-ttu-id="da756-118">[[オブジェクト エクスプローラーの詳細] ペイン](object-explorer-details-pane.md)</span><span class="sxs-lookup"><span data-stu-id="da756-118">[Object Explorer Details Pane](object-explorer-details-pane.md)</span></span>|  
|<span data-ttu-id="da756-119">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でカスタム レポートを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="da756-119">Describes ways to run custom reports in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>|[<span data-ttu-id="da756-120">Management Studio におけるカスタム レポート</span><span class="sxs-lookup"><span data-stu-id="da756-120">Custom Reports in Management Studio</span></span>](custom-reports-in-management-studio.md)|  
  
  
