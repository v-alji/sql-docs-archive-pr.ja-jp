---
title: '[オブジェクトの選択] (オブジェクト エクスプローラー) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.common.selectobjects.f1
ms.assetid: 692477fe-dd7c-403d-acd2-bb108b6077f1
author: stevestein
ms.author: sstein
ms.openlocfilehash: ceec604d9fe07b339af11ed69226d41a7f616678
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711538"
---
# <a name="select-objects-object-explorer"></a><span data-ttu-id="b4826-102">[オブジェクトの選択] (オブジェクト エクスプローラー)</span><span class="sxs-lookup"><span data-stu-id="b4826-102">Select Objects (Object Explorer)</span></span>
  <span data-ttu-id="b4826-103">**[オブジェクトの選択]** ダイアログ ボックスを使用すると、オブジェクトを別のダイアログ ボックスの一覧に追加できます。</span><span class="sxs-lookup"><span data-stu-id="b4826-103">Use the **Select Objects** dialog box to add an object to a list in another dialog box.</span></span> <span data-ttu-id="b4826-104">ダイアログ ボックスを開いた方法に応じて、ダイアログ ボックスのタイトルおよび使用できるオプションが異なります。</span><span class="sxs-lookup"><span data-stu-id="b4826-104">The dialog box title and the options available in the dialog box depend upon how it was opened.</span></span> <span data-ttu-id="b4826-105">利用可能なオプションだけが表示されます。たとえば、新しいオブジェクトの所有者を選択する場合は、利用可能なログインだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4826-105">Only available options appear; for instance, only logins are available when you are selecting an owner for a new object.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b4826-106">オプション</span><span class="sxs-lookup"><span data-stu-id="b4826-106">Options</span></span>  
 <span data-ttu-id="b4826-107">**[以下のオブジェクトの種類を選択]**</span><span class="sxs-lookup"><span data-stu-id="b4826-107">**Select these object types**</span></span>  
 <span data-ttu-id="b4826-108">選択するオブジェクトの種類の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="b4826-108">Displays a list of the types of which the objects to be selected belong.</span></span> <span data-ttu-id="b4826-109">種類には、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レベルやデータベース レベルのプリンシパルおよびセキュリティ保護可能なリソースが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b4826-109">The types include [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] level and database level principals and securables.</span></span> <span data-ttu-id="b4826-110">このボックスには、 **[オブジェクトの種類]** ボタンをクリックして表示される **[オブジェクトの種類を選択]** ダイアログ ボックスで選択した内容が入力されます。</span><span class="sxs-lookup"><span data-stu-id="b4826-110">This box is populated from the selections made from the **Select Object Types** dialog box, accessed from the **Objects Type** button.</span></span>  
  
 <span data-ttu-id="b4826-111">**[追加するオブジェクト名の入力]**</span><span class="sxs-lookup"><span data-stu-id="b4826-111">**Enter the object names to select**</span></span>  
 <span data-ttu-id="b4826-112">選択するオブジェクトの名前のリストをセミコロン区切りで入力します。</span><span class="sxs-lookup"><span data-stu-id="b4826-112">Enter a semicolon-separated list of names of the objects to be selected.</span></span> <span data-ttu-id="b4826-113">選択するオブジェクトの種類は、 **[以下のオブジェクトの種類を選択]** ボックスに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4826-113">Objects to be selected must be of a type listed in the **Select these object types** box.</span></span> <span data-ttu-id="b4826-114">オブジェクトは、 **[参照]** ボタンをクリックしてアクセスできる一覧から選択できます。</span><span class="sxs-lookup"><span data-stu-id="b4826-114">Objects can be selected from a list accessed by clicking the **Browse** button.</span></span>  
  
 <span data-ttu-id="b4826-115">**[オブジェクトの種類]**</span><span class="sxs-lookup"><span data-stu-id="b4826-115">**Object Types**</span></span>  
 <span data-ttu-id="b4826-116">オブジェクトの種類の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="b4826-116">Displays a list of object types.</span></span> <span data-ttu-id="b4826-117">種類に対応するチェック ボックスをオンにすることにより、種類を 1 つ以上選択できます。</span><span class="sxs-lookup"><span data-stu-id="b4826-117">Select one or more by selecting the check box corresponding to the type.</span></span>  
  
 <span data-ttu-id="b4826-118">**[名前の確認]**</span><span class="sxs-lookup"><span data-stu-id="b4826-118">**Check Names**</span></span>  
 <span data-ttu-id="b4826-119">**[追加するオブジェクト名の入力]** ボックスでオブジェクト名を確認します。</span><span class="sxs-lookup"><span data-stu-id="b4826-119">Validates the object names in the **Enter the object names to select** box.</span></span> <span data-ttu-id="b4826-120">無効なオブジェクト名が表示されている場合は、 **[名前が見つかりません]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4826-120">If an object name that is not valid is listed, the **Name not Found** dialog box is presented.</span></span> <span data-ttu-id="b4826-121">このダイアログ ボックスで、選択するオブジェクトの一覧の名前を修正または削除できます。</span><span class="sxs-lookup"><span data-stu-id="b4826-121">With this dialog box, the name can be corrected or removed from the list of objects to select.</span></span>  
  
 <span data-ttu-id="b4826-122">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="b4826-122">**Browse**</span></span>  
 <span data-ttu-id="b4826-123">**[オブジェクトの参照]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4826-123">Presents the **Browse for Objects** dialog box.</span></span> <span data-ttu-id="b4826-124">このダイアログ ボックスには、 **[以下のオブジェクトの種類を選択]** ボックスに示される種類のオブジェクトの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4826-124">This contains a list of objects of the types listed in the **Select These Object Types** box.</span></span> <span data-ttu-id="b4826-125">この一覧からオブジェクトを選択するには、対応するチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="b4826-125">Select objects from this list by selecting the corresponding check boxes.</span></span>  
  
  
