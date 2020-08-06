---
title: SQL Server Management Studio のツール ウィンドウ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], tool windows
- tool windows [SQL Server Management Studio]
ms.assetid: d3be5062-234c-43a8-8d47-cce111dd3c25
author: stevestein
ms.author: sstein
ms.openlocfilehash: c3cc4c44e00e4c16a6211086b16861f3e9233357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711525"
---
# <a name="tool-windows-in-sql-server-management-studio"></a><span data-ttu-id="f5623-102">SQL Server Management Studio のツール ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="f5623-102">Tool Windows in SQL Server Management Studio</span></span>
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="f5623-103">には、開発と管理のあらゆる段階で使用できる強力なツール ウィンドウが数多く用意されています。</span><span class="sxs-lookup"><span data-stu-id="f5623-103">provides many powerful tool windows for all phases of development and administration.</span></span> <span data-ttu-id="f5623-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のあらゆるコンポーネントで使用できるツールもあれば、特定のコンポーネントだけで使用できるツールもあります。</span><span class="sxs-lookup"><span data-stu-id="f5623-104">Some tools can be used on any [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] component, and others are for certain components only.</span></span> <span data-ttu-id="f5623-105">次の表に、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のすべてのコンポーネントで使用できるツールを示します。</span><span class="sxs-lookup"><span data-stu-id="f5623-105">The following table identifies the tools that can be used for all components of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f5623-106">**ツール**</span><span class="sxs-lookup"><span data-stu-id="f5623-106">**Tool**</span></span>|<span data-ttu-id="f5623-107">**目的**</span><span class="sxs-lookup"><span data-stu-id="f5623-107">**Purpose**</span></span>|  
|<span data-ttu-id="f5623-108">[[オブジェクト エクスプローラー]](object/object-explorer.md)</span><span class="sxs-lookup"><span data-stu-id="f5623-108">[Object Explorer](object/object-explorer.md)</span></span>|<span data-ttu-id="f5623-109">サーバー内の表示、オブジェクトの作成と検索、データ ソースの管理、ログの表示を行います。</span><span class="sxs-lookup"><span data-stu-id="f5623-109">Browse servers, create and locate objects, manage data sources, and view logs.</span></span> <span data-ttu-id="f5623-110">このツールには、 **[表示]** メニューからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f5623-110">This tool is accessed from the **View** menu.</span></span>|  
|[<span data-ttu-id="f5623-111">ソリューション エクスプローラー</span><span class="sxs-lookup"><span data-stu-id="f5623-111">Solution Explorer</span></span>](solution/solution-explorer.md)|<span data-ttu-id="f5623-112">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] スクリプトというプロジェクトにスクリプトや関連する接続情報を格納して整理します。</span><span class="sxs-lookup"><span data-stu-id="f5623-112">Store and organize scripts and related connection information in projects called [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Scripts.</span></span> <span data-ttu-id="f5623-113">複数の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] スクリプトをソリューションとして格納することや、ソース管理を使用してスクリプトの開発過程を管理することも可能です。</span><span class="sxs-lookup"><span data-stu-id="f5623-113">You can store several [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Scripts as Solutions and use source control to manage scripts as they evolve over time.</span></span> <span data-ttu-id="f5623-114">このツールには、 **[表示]** メニューからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f5623-114">This tool is accessed from the **View** menu.</span></span>|  
|[<span data-ttu-id="f5623-115">テンプレート エクスプローラー</span><span class="sxs-lookup"><span data-stu-id="f5623-115">Template Explorer</span></span>](template/template-explorer.md)|<span data-ttu-id="f5623-116">既存のテンプレートに基づいてクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="f5623-116">Create queries based on existing templates.</span></span> <span data-ttu-id="f5623-117">カスタム クエリを作成することや、既存のテンプレートをそれぞれのシナリオに合わせて変更することも可能です。</span><span class="sxs-lookup"><span data-stu-id="f5623-117">You can also create your custom queries or alter the existing templates to fit your scenarios.</span></span> <span data-ttu-id="f5623-118">このツールには、 **[表示]** メニューからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f5623-118">This tool is accessed from the **View** menu.</span></span>|  
|[<span data-ttu-id="f5623-119">ダイナミック ヘルプを表示する</span><span class="sxs-lookup"><span data-stu-id="f5623-119">Dynamic Help</span></span>](sql-server-management-studio-ssms.md)|<span data-ttu-id="f5623-120">コンポーネントのクリックやコードの入力に対応して、関連するヘルプ トピックの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="f5623-120">Show a list of related Help topics as you click on a component or type code.</span></span>|  
  
 <span data-ttu-id="f5623-121">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] の各ツールは、連携して機能します。</span><span class="sxs-lookup"><span data-stu-id="f5623-121">The tools in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] work together.</span></span> <span data-ttu-id="f5623-122">たとえば、次のように操作できます。</span><span class="sxs-lookup"><span data-stu-id="f5623-122">For example, you can:</span></span>  
  
-   <span data-ttu-id="f5623-123">オブジェクト エクスプローラーでサーバーを登録する。</span><span class="sxs-lookup"><span data-stu-id="f5623-123">Register a server with Object Explorer.</span></span>  
  
-   <span data-ttu-id="f5623-124">特定のデータベースに接続している [SQL エディター] ウィンドウをオブジェクト エクスプローラーから開く。</span><span class="sxs-lookup"><span data-stu-id="f5623-124">Open a SQL Editor window connected to a specific database from Object Explorer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5623-125">参照</span><span class="sxs-lookup"><span data-stu-id="f5623-125">See Also</span></span>  
 <span data-ttu-id="f5623-126">[SQL Server Management Studio の使用 [SQL Server]](../database-engine/use-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="f5623-126">[Use SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md)</span></span>  
  
  
