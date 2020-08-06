---
title: テンプレートを開く | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- templates [Transact-SQL], opening
- opening templates
ms.assetid: 605b0f4c-5ba1-4249-ad1c-6341df77cd7a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 43b75d68fafea759e4d7873c1fb738d7964dcf57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642477"
---
# <a name="open-a-template"></a><span data-ttu-id="f8cf2-102">テンプレートを開く</span><span class="sxs-lookup"><span data-stu-id="f8cf2-102">Open a Template</span></span>
  <span data-ttu-id="f8cf2-103">テンプレート エクスプローラーからテンプレートを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="f8cf2-103">You can open a template from Template Explorer.</span></span>  
  
## <a name="to-open-a-template-from-template-explorer"></a><span data-ttu-id="f8cf2-104">テンプレート エクスプローラーからテンプレートを開くには</span><span class="sxs-lookup"><span data-stu-id="f8cf2-104">To open a template from Template Explorer</span></span>  
 <span data-ttu-id="f8cf2-105">テンプレート エクスプローラーからテンプレートを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="f8cf2-105">You can open templates from the Template Explorer.</span></span>  
  
1.  <span data-ttu-id="f8cf2-106">テンプレート エクスプローラーを開くには、 **[表示]** メニューの **[テンプレート エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f8cf2-106">To open Template Explorer, on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="f8cf2-107">テンプレート カテゴリの一覧で、開こうとしているテンプレートを含むカテゴリを展開します。</span><span class="sxs-lookup"><span data-stu-id="f8cf2-107">In the list of template categories, expand the category that contains the template you want to open.</span></span>  
  
3.  <span data-ttu-id="f8cf2-108">テンプレートを開くには、次の 3 とおりの方法があります。</span><span class="sxs-lookup"><span data-stu-id="f8cf2-108">There are three ways to open the template:</span></span>  
  
    1.  <span data-ttu-id="f8cf2-109">テンプレートをダブルクリックしてコード エディター ウィンドウで開きます。</span><span class="sxs-lookup"><span data-stu-id="f8cf2-109">Double-click the template to open it in a code editor window.</span></span>  
  
    2.  <span data-ttu-id="f8cf2-110">テンプレートを右クリックして **[開く]** を選択し、コード エディター ウィンドウで開きます。</span><span class="sxs-lookup"><span data-stu-id="f8cf2-110">Right-click the template and select **Open** to open it in a code editor window.</span></span>  
  
    3.  <span data-ttu-id="f8cf2-111">テンプレートをコード エディター ウィンドウにドラッグし、テンプレート コードをエディター ウィンドウの内容に追加します。</span><span class="sxs-lookup"><span data-stu-id="f8cf2-111">Drag the template into a code editor window to add the template code to the contents of the editor window.</span></span>  
  
 <span data-ttu-id="f8cf2-112">テンプレートを開いた後、 **[テンプレート パラメーターの値の指定]** ダイアログ ボックスでテンプレート パラメーターを適切な値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f8cf2-112">After the template is open, use the **Replace Template Parameters** dialog box to replace the template parameters with your values.</span></span>  
  
 <span data-ttu-id="f8cf2-113">テンプレートを開いて新しいエディター ウィンドウが起動する場合、そのウィンドウは、現在のアクティブな接続の資格情報によって開きます。</span><span class="sxs-lookup"><span data-stu-id="f8cf2-113">If opening a template launches a new editor window, the window will open with the credentials of the current active connection.</span></span> <span data-ttu-id="f8cf2-114">たとえば、CREATE DATABASE テンプレートを開くときに、オブジェクト エクスプローラーで [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスにフォーカスがあると、そのインスタンスへの接続を使用して新しいエディター ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="f8cf2-114">For example, if you are focused on an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in Object Explorer when you open the CREATE DATABASE template, a new editor window will be opened using a connection to that instance.</span></span> <span data-ttu-id="f8cf2-115">アクティブな接続がない場合は、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] によってログイン ダイアログが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8cf2-115">If there is no active connection, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] will present a login dialog.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8cf2-116">参照</span><span class="sxs-lookup"><span data-stu-id="f8cf2-116">See Also</span></span>  
 <span data-ttu-id="f8cf2-117">[テンプレートエクスプローラー](template-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="f8cf2-117">[Template Explorer](template-explorer.md) </span></span>  
 [<span data-ttu-id="f8cf2-118">テンプレート パラメーターの置換</span><span class="sxs-lookup"><span data-stu-id="f8cf2-118">Replace Template Parameters</span></span>](replace-template-parameters.md)  
  
  
