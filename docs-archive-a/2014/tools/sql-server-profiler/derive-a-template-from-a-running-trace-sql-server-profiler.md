---
title: 実行中のトレースからのテンプレートの作成 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], traces
- trace templates [SQL Server]
ms.assetid: 25a3b845-affb-4b2a-a382-198a4bdd9ad1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 72744ce942cc49038129cf6064349e23c3e9a41d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711250"
---
# <a name="derive-a-template-from-a-running-trace-sql-server-profiler"></a><span data-ttu-id="2db2c-102">実行中のトレースからのテンプレートの作成 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="2db2c-102">Derive a Template from a Running Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="2db2c-103">このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、実行中の既存のトーレスからトレース テンプレートを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="2db2c-103">This topic describes how to create a trace template from an existing trace while it is running by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-derive-a-template-from-a-running-trace"></a><span data-ttu-id="2db2c-104">実行中のトレースからテンプレートを作成するには</span><span class="sxs-lookup"><span data-stu-id="2db2c-104">To derive a template from a running trace</span></span>  
  
1.  <span data-ttu-id="2db2c-105">目的のトレースが表示されているウィンドウに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="2db2c-105">If necessary, switch to the window that contains the trace.</span></span>  
  
2.  <span data-ttu-id="2db2c-106">**[ファイル]** メニューの **[名前を付けて保存]** をポイントし、 **[トレース テンプレート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2db2c-106">On the **File** menu, point to **Save As**, and then click **Trace Template**.</span></span>  
  
3.  <span data-ttu-id="2db2c-107">名前を入力するか、または一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="2db2c-107">Type a name or select one from the list.</span></span> <span data-ttu-id="2db2c-108">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2db2c-108">Click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2db2c-109">既存のテンプレート ファイルを選択した場合は、ファイルを上書きするかどうかを確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2db2c-109">If you select an existing template file, you are asked if you want to overwrite the file.</span></span> <span data-ttu-id="2db2c-110">選択できるのは、ユーザー定義のテンプレートだけです。</span><span class="sxs-lookup"><span data-stu-id="2db2c-110">You can only select a user-defined template.</span></span> <span data-ttu-id="2db2c-111">定義済みのシステム トレース テンプレートは上書きできません。</span><span class="sxs-lookup"><span data-stu-id="2db2c-111">Predefined system trace templates cannot be overwritten.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2db2c-112">参照</span><span class="sxs-lookup"><span data-stu-id="2db2c-112">See Also</span></span>  
 <span data-ttu-id="2db2c-113">[SQL Server プロファイラーのテンプレートと権限](sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="2db2c-113">[SQL Server Profiler Templates and Permissions](sql-server-profiler-templates-and-permissions.md) </span></span>  
 <span data-ttu-id="2db2c-114">[トレース テンプレートの作成 &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="2db2c-114">[Create a Trace Template &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="2db2c-115">[トレース テンプレートの変更 &#40;SQL Server Profiler&#41;](../../database-engine/modify-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="2db2c-115">[Modify a Trace Template &#40;SQL Server Profiler&#41;](../../database-engine/modify-a-trace-template-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="2db2c-116">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="2db2c-116">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
