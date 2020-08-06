---
title: テンプレート エクスプローラー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.wb.templates.f1
- sql12.swb.templates.explorer.f1
helpviewer_keywords:
- templates [SQL Server]
- SQL Server Management Studio [SQL Server], Template Explorer
- Template Explorer
- templates [Transact-SQL]
- templates [SQL Server], Template Explorer
ms.assetid: b9ee55c5-bb44-4f76-90ac-792d8d83b4c8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35e7ee1e6261c759580df3a836f9cc4b500a77ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642472"
---
# <a name="template-explorer"></a><span data-ttu-id="f5d24-102">テンプレート エクスプローラー</span><span class="sxs-lookup"><span data-stu-id="f5d24-102">Template Explorer</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f5d24-103">にはさまざまなテンプレートがあります。</span><span class="sxs-lookup"><span data-stu-id="f5d24-103">provides a variety of templates.</span></span> <span data-ttu-id="f5d24-104">テンプレートは、データベース内のオブジェクトを簡単に作成するための SQL スクリプトを含む、定型的なファイルです。</span><span class="sxs-lookup"><span data-stu-id="f5d24-104">Templates are boilerplate files containing SQL scripts that help you create objects in a database.</span></span> <span data-ttu-id="f5d24-105">テンプレートエクスプローラーを初めて開くと、テンプレートのコピーが C:\Users のユーザーのフォルダー (AppData\Roaming\Microsoft\SQL Server Management Studio\120\templates) に配置されます。</span><span class="sxs-lookup"><span data-stu-id="f5d24-105">The first time the template explorer is opened, a copy of the templates are placed in the user's folder in C:\Users, under AppData\Roaming\Microsoft\SQL Server Management Studio\120\Templates.</span></span>  
  
 <span data-ttu-id="f5d24-106">使用できるテンプレートをテンプレート エクスプローラーで参照し、テンプレートを開いて、コードをコード エディター ウィンドウに読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="f5d24-106">You can browse the available templates in Template Explorer, then open a template to incorporate the code into a code editor window.</span></span> <span data-ttu-id="f5d24-107">また、カスタム テンプレートを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="f5d24-107">You can also create custom templates.</span></span>  
  
## <a name="benefits-of-templates"></a><span data-ttu-id="f5d24-108">テンプレートの利点</span><span class="sxs-lookup"><span data-stu-id="f5d24-108">Benefits of Templates</span></span>  
 <span data-ttu-id="f5d24-109">テンプレートはソリューション、プロジェクト、および各種のコード エディターに対して使用できます。</span><span class="sxs-lookup"><span data-stu-id="f5d24-109">Templates are available for solutions, projects, and various types of code editors.</span></span> <span data-ttu-id="f5d24-110">テンプレートは、データベース、テーブル、ビュー、インデックス、ストアド プロシージャ、トリガー、統計、関数のようなオブジェクトを作成するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="f5d24-110">Templates are available to create objects like databases, tables, views, indexes, stored procedures, triggers, statistics, and functions.</span></span> <span data-ttu-id="f5d24-111">さらに、拡張プロパティ、リンク サーバー、ログイン、ロール、ユーザーを作成してサーバーを管理するために役立つテンプレートや、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のテンプレートもあります。</span><span class="sxs-lookup"><span data-stu-id="f5d24-111">In addition, there are templates that help you to manage your server by creating extended properties, linked servers, logins, roles, users, and templates for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f5d24-112">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で提供されるテンプレート スクリプトにはパラメーターを指定できるので、コードをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="f5d24-112">The template scripts provided with [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] contain parameters to help you customize the code.</span></span> <span data-ttu-id="f5d24-113">テンプレートを開くときに、 **[テンプレート パラメーターの置換]** ダイアログ ボックスでスクリプトに値を挿入します。</span><span class="sxs-lookup"><span data-stu-id="f5d24-113">When you open a template, Use the **Replace Template Parameters** dialog box to insert values into the script.</span></span>  
  
 <span data-ttu-id="f5d24-114">頻繁に実行するタスクについては、カスタム テンプレートを作成します。</span><span class="sxs-lookup"><span data-stu-id="f5d24-114">Create custom templates for tasks you perform frequently.</span></span> <span data-ttu-id="f5d24-115">カスタム スクリプトは、既存のフォルダーに入れるか、新しいフォルダーを作成して整理します。</span><span class="sxs-lookup"><span data-stu-id="f5d24-115">Organize your custom scripts into the existing folders or create a new folder structure.</span></span>  
  
 <span data-ttu-id="f5d24-116">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターもコード スニペットをサポートしており、スクリプト内の特定の場所を右クリックして、そこにコード スニペットを挿入できます。</span><span class="sxs-lookup"><span data-stu-id="f5d24-116">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query editor also supports code snippets, which can be inserted at specific locations in a script by right-clicking at that location.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="f5d24-117">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="f5d24-117">Related Tasks</span></span>  
 <span data-ttu-id="f5d24-118">テンプレートの基礎知識については、次の各トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5d24-118">Use the following topics to get started with templates</span></span>  
  
|<span data-ttu-id="f5d24-119">**説明**</span><span class="sxs-lookup"><span data-stu-id="f5d24-119">**Description**</span></span>|<span data-ttu-id="f5d24-120">**トピック**</span><span class="sxs-lookup"><span data-stu-id="f5d24-120">**Topic**</span></span>|  
|---------------------|---------------|  
|<span data-ttu-id="f5d24-121">テンプレートからコード エディター ウィンドウにコードを読み込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f5d24-121">Describes how to incorporate the code from a template into a code editor window.</span></span>|[<span data-ttu-id="f5d24-122">テンプレートを開く</span><span class="sxs-lookup"><span data-stu-id="f5d24-122">Open a Template</span></span>](open-a-template.md)|  
|<span data-ttu-id="f5d24-123">コード エディターでテンプレートを開いてからテンプレート パラメーターの値を置換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f5d24-123">Describes how to replace template parameter values after opening a template in a code editor.</span></span>|[<span data-ttu-id="f5d24-124">テンプレート パラメーターの置換</span><span class="sxs-lookup"><span data-stu-id="f5d24-124">Replace Template Parameters</span></span>](replace-template-parameters.md)|  
  
  
