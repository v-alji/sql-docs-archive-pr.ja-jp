---
title: 'タスク 7: 複合ドメインを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ae778647-1df0-4952-9a69-0ef6177eea9c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 42936d25e267bcad5ba8ae512750f9e12f041579
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631389"
---
# <a name="task-7-creating-a-composite-domain"></a><span data-ttu-id="b7c03-102">タスク 7: 複合ドメインを作成する</span><span class="sxs-lookup"><span data-stu-id="b7c03-102">Task 7: Creating a Composite Domain</span></span>
  <span data-ttu-id="b7c03-103">このタスクでは、address **Line**、 **City**、 **State**、および**Zip**の各ドメインで構成される、**アドレス検証**という複合ドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="b7c03-103">In this task, you create a composite domain, **Address Validation**, which comprises **Address Line**, **City**, **State**, and **Zip** domains.</span></span> <span data-ttu-id="b7c03-104">複合ドメインでは、ルール内の複数のドメインに関するクロスドメイン ルールを定義できます。</span><span class="sxs-lookup"><span data-stu-id="b7c03-104">A composite domain lets you define a cross-domain rule that involves multiple domains in a rule.</span></span> <span data-ttu-id="b7c03-105">複合ドメインには、フィールド値を複数のドメインに解析できるなどの利点があります。</span><span class="sxs-lookup"><span data-stu-id="b7c03-105">There are other advantages to a composite domain such as being able to parse a field value into multiple domains.</span></span>  <span data-ttu-id="b7c03-106">たとえば、氏名フィールドの値を、名、ミドル ネーム、および姓の個別のドメインに解析できます。</span><span class="sxs-lookup"><span data-stu-id="b7c03-106">For example, a value for a Full Name field can be parsed into separate First Name, Middle Name, and Last Name domains.</span></span> <span data-ttu-id="b7c03-107">このチュートリアルでは、クロスドメイン ルールのみを定義します。</span><span class="sxs-lookup"><span data-stu-id="b7c03-107">In this tutorial, you only define a cross-domain rule.</span></span> <span data-ttu-id="b7c03-108">詳細について[は、「複合ドメインの管理](https://msdn.microsoft.com/library/hh510399.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7c03-108">See [Managing a Composite Domain](https://msdn.microsoft.com/library/hh510399.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="b7c03-109">左側のウィンドウで、ツールバーの [**複合ドメインの作成**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b7c03-109">In the left pane, click **Create a composite domain** button on the toolbar.</span></span>  
  
     <span data-ttu-id="b7c03-110">![[複合ドメインの作成] ツール バー ボタン](../../2014/tutorials/media/et-creatingacompositedomain-01.jpg "[複合ドメインの作成] ツール バー ボタン")</span><span class="sxs-lookup"><span data-stu-id="b7c03-110">![Create a Composite Domain Toolbar Button](../../2014/tutorials/media/et-creatingacompositedomain-01.jpg "Create a Composite Domain Toolbar Button")</span></span>  
  
2.  <span data-ttu-id="b7c03-111">**複合ドメイン名**の**アドレス検証**を入力します。</span><span class="sxs-lookup"><span data-stu-id="b7c03-111">Enter **Address Validation** for the **Composite Domain Name**.</span></span>  
  
     <span data-ttu-id="b7c03-112">![アドレス検証複合ドメイン](../../2014/tutorials/media/et-creatingacompositedomain-02.jpg "アドレス検証複合ドメイン")</span><span class="sxs-lookup"><span data-stu-id="b7c03-112">![Address Validation Composite Domain](../../2014/tutorials/media/et-creatingacompositedomain-02.jpg "Address Validation Composite Domain")</span></span>  
  
3.  <span data-ttu-id="b7c03-113">[ドメイン] ボックスの一覧から [ **Address Line**]、[ **City**]、[ **State**]、および [ **Zip** ] を選択し、**右矢印**をクリックして [**複合ドメイン内のドメイン**] の一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="b7c03-113">From the domain list select **Address Line**, **City**, **State**, and **Zip** and click **right arrow** to add them to the **Domains in Composite Domain** list.</span></span>  
  
4.  <span data-ttu-id="b7c03-114">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="b7c03-114">Click **OK** to close the dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="b7c03-115">次の手順</span><span class="sxs-lookup"><span data-stu-id="b7c03-115">Next Step</span></span>  
 [<span data-ttu-id="b7c03-116">タスク 8: 複合ドメイン ルールを作成する</span><span class="sxs-lookup"><span data-stu-id="b7c03-116">Task 8: Creating a Composite Domain Rule</span></span>](../../2014/tutorials/task-8-creating-a-composite-domain-rule.md)  
  
  
