---
title: トレース定義の既定値の設定 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], defaults
ms.assetid: ab9fc570-797d-411e-814f-1c46d2d5feae
author: stevestein
ms.author: sstein
ms.openlocfilehash: 90b031de11f166a40e79ce4289eba508ba923c52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632235"
---
# <a name="set-trace-definition-defaults-sql-server-profiler"></a><span data-ttu-id="37e86-102">トレース定義の既定値の設定 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="37e86-102">Set Trace Definition Defaults (SQL Server Profiler)</span></span>
  <span data-ttu-id="37e86-103">トレース定義の既定値は、プロバイダーまたはサーバーごとに使用される既定のトレース テンプレートです。</span><span class="sxs-lookup"><span data-stu-id="37e86-103">The trace definition default is the default trace template that is used for each provider or server.</span></span> <span data-ttu-id="37e86-104">既定のトレース テンプレートは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]に設定できます。</span><span class="sxs-lookup"><span data-stu-id="37e86-104">You can set default trace templates for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
### <a name="to-set-trace-definition-defaults"></a><span data-ttu-id="37e86-105">トレース定義の既定値を設定するには</span><span class="sxs-lookup"><span data-stu-id="37e86-105">To set trace definition defaults</span></span>  
  
1.  <span data-ttu-id="37e86-106">**[ファイル]** メニューの **[テンプレート]** をクリックし、 **[テンプレートの編集] をクリックします。**</span><span class="sxs-lookup"><span data-stu-id="37e86-106">On the **File** menu, select **Templates**, and then click **Edit Template.**</span></span>  
  
2.  <span data-ttu-id="37e86-107">**[トレース テンプレートのプロパティ]** ダイアログ ボックスの **[全般]** タブで、 **[サーバーの種類の選択]** ボックスの一覧からサーバーの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="37e86-107">In the **Trace Template Properties** dialog box, on the **General**tab, select a server type from the **Select server type**list.</span></span>  
  
3.  <span data-ttu-id="37e86-108">**[テンプレート名の選択]** ボックスの一覧で、トレース定義の既定値として使用するテンプレートの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="37e86-108">In the **Select template name**list, select the name of the template that you want to use as the trace definition default.</span></span>  
  
4.  <span data-ttu-id="37e86-109">**[選択したサーバーの種類に対する既定のテンプレートとして使用する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="37e86-109">Select **Use as a default template for selected server type**.</span></span>  
  
5.  <span data-ttu-id="37e86-110">必要な場合は、 **[イベントの選択]** タブをクリックして、テンプレートを編集します。</span><span class="sxs-lookup"><span data-stu-id="37e86-110">If necessary, click the **Events Selection**tab to modify the template.</span></span>  
  
6.  <span data-ttu-id="37e86-111">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="37e86-111">Click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37e86-112">参照</span><span class="sxs-lookup"><span data-stu-id="37e86-112">See Also</span></span>  
 <span data-ttu-id="37e86-113">[SQL Server Profiler のテンプレート](sql-server-profiler-templates.md) </span><span class="sxs-lookup"><span data-stu-id="37e86-113">[SQL Server Profiler Templates](sql-server-profiler-templates.md) </span></span>  
 [<span data-ttu-id="37e86-114">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="37e86-114">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
