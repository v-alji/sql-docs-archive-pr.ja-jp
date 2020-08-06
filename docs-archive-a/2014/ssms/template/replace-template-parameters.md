---
title: テンプレート パラメーターを置き換える | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.templates.replaceparameters.f1
helpviewer_keywords:
- template parameters [Template Explorer]
- templates [Transact-SQL], replacing parameters
- Replace (Query) Template Parameters dialog box
- replacing template parameters
ms.assetid: 1234aa14-3464-4a3e-922a-5cfb8fb23627
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1d87b17a110efe118f7796487448e4d3bae30375
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642478"
---
# <a name="replace-template-parameters"></a><span data-ttu-id="584a5-102">[テンプレート パラメーターの置換]</span><span class="sxs-lookup"><span data-stu-id="584a5-102">Replace Template Parameters</span></span>
  <span data-ttu-id="584a5-103">テンプレートには、テンプレートを使用するたびに実装固有の値に置き換えることができるパラメーターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="584a5-103">Templates contain parameters that can be replaced by implementation-specific values each time the template is used.</span></span> <span data-ttu-id="584a5-104">コード エディターでテンプレートを開いた後、パラメーターを実装に関する値に置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="584a5-104">After opening a template in a code editor, you can replace the parameters with values relevant to your implementation.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="584a5-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="584a5-105">Before You Begin</span></span>  
 <span data-ttu-id="584a5-106">**[テンプレート パラメーターの値の指定]** ダイアログは、3 つの列を含むグリッドです。</span><span class="sxs-lookup"><span data-stu-id="584a5-106">The **Specify Values for Template Parameters** dialog is a grid with three columns.</span></span> <span data-ttu-id="584a5-107">**[パラメーター]** 列と **[種類]** 列は読み取り専用であり、変更できません。</span><span class="sxs-lookup"><span data-stu-id="584a5-107">The **Parameter** and **Type** columns are read-only and cannot be changed.</span></span> <span data-ttu-id="584a5-108">**[値]** 列の内容を確認し、既定値を実装に応じた値に変更します。</span><span class="sxs-lookup"><span data-stu-id="584a5-108">Review the contents of the **Value** column, and change any of the defaults to values appropriate for your implementation.</span></span>  
  
 <span data-ttu-id="584a5-109">このダイアログ ボックスを使用するには、スクリプトに山かっこ (`< >`) で囲んだパラメーターを `<`*parameter_name*`,` *data_type*`,` *default_value*`>`の形式で含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="584a5-109">To use this dialog box, you must have parameters in your script enclosed in angle brackets (`< >`) in the format `<`*parameter_name*`,` *data_type*`,` *default_value*`>`.</span></span>  
  
## <a name="replace-template-parameters"></a><span data-ttu-id="584a5-110">[テンプレート パラメーターの置換]</span><span class="sxs-lookup"><span data-stu-id="584a5-110">Replace Template Parameters</span></span>  
 <span data-ttu-id="584a5-111">コード エディター ウィンドウでテンプレートを開いた後、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="584a5-111">After opening the template in a code editor window:</span></span>  
  
1.  <span data-ttu-id="584a5-112">**[クエリ]** メニューの **[テンプレート パラメーターの値の指定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="584a5-112">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span>  
  
2.  <span data-ttu-id="584a5-113">**[テンプレート パラメーターの値の指定]** ダイアログ ボックスの **[値]** 列には、各パラメーターの推奨値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="584a5-113">In the **Specify Values for Template Parameters** dialog box, the **Values** column contains a suggested value for each parameter.</span></span> <span data-ttu-id="584a5-114">推奨値をそのまま使用するか、または別の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="584a5-114">Accept the value or replace it with a new value.</span></span>  
  
3.  <span data-ttu-id="584a5-115">**[OK]** をクリックして **[テンプレート パラメーターを置き換える]** ダイアログ ボックスを閉じ、クエリ エディターでスクリプトを変更します。</span><span class="sxs-lookup"><span data-stu-id="584a5-115">Click **OK** to close the **Replace Template Parameters** dialog box and modify the script in the query editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="584a5-116">参照</span><span class="sxs-lookup"><span data-stu-id="584a5-116">See Also</span></span>  
 <span data-ttu-id="584a5-117">[テンプレートエクスプローラー](template-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="584a5-117">[Template Explorer](template-explorer.md) </span></span>  
 [<span data-ttu-id="584a5-118">テンプレートを開く</span><span class="sxs-lookup"><span data-stu-id="584a5-118">Open a Template</span></span>](open-a-template.md)  
  
  
