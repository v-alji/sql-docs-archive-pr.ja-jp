---
title: '[オブジェクトの依存関係] | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.common.objectdependencies.f1
ms.assetid: c63d1160-3f3d-45df-99be-6fe081125fb5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 13d1775f1e4e6885fe56a43ce40c4ac155c5b361
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741538"
---
# <a name="object-dependencies"></a><span data-ttu-id="a3e88-102">[オブジェクトの依存関係]</span><span class="sxs-lookup"><span data-stu-id="a3e88-102">Object Dependencies</span></span>
  <span data-ttu-id="a3e88-103">一部のデータベース オブジェクトには、他のデータベース オブジェクトと依存関係があります。</span><span class="sxs-lookup"><span data-stu-id="a3e88-103">Some database objects have dependencies upon other database objects.</span></span> <span data-ttu-id="a3e88-104">たとえば、ビューとストアド プロシージャは、そのビューまたはプロシージャが返すデータを格納するテーブルの存在に依存します。</span><span class="sxs-lookup"><span data-stu-id="a3e88-104">For example, views and stored procedures depend upon the existence of tables that contain the data returned by the view or procedure.</span></span> <span data-ttu-id="a3e88-105">現在のオブジェクトの **[オブジェクトの依存関係]\([全般] ページ)** には、オブジェクトが正常に動作するために必要なデータベース オブジェクト、および選択されているオブジェクトに依存するオブジェクトの両方が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3e88-105">The **Object Dependencies (General Page)** for the current object lists both the database objects that must be present for the object to function properly and the objects that depend upon the selected object.</span></span> <span data-ttu-id="a3e88-106">オブジェクトは、その定義で別のオブジェクトを参照する場合 (この定義はシステム カタログに格納されます)、 *参照元エンティティ*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="a3e88-106">An object that references another object in its definition and that definition is stored in the system catalog is called a *referencing entity*.</span></span> <span data-ttu-id="a3e88-107">別のオブジェクトによって参照されるオブジェクトは、 *参照先エンティティ*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="a3e88-107">An object that is referred to by another object is called a *referenced entity*.</span></span>  
  
 <span data-ttu-id="a3e88-108">現在のオブジェクトの **[オブジェクトの依存関係]\([詳細設定] ページ)** には、オブジェクトに依存する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース オブジェクトおよび [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] オブジェクトが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3e88-108">The **Object Dependencies (Advanced Page)** for the current object lists the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database objects and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] objects that depend on the object.</span></span> <span data-ttu-id="a3e88-109">それらのオブジェクトは、別のサーバーに格納されている場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a3e88-109">The objects may be stored on different servers.</span></span>  
  
 <span data-ttu-id="a3e88-110">このダイアログ ボックスを使用すると、選択されているオブジェクトを変更または削除する前に依存関係について理解できます。</span><span class="sxs-lookup"><span data-stu-id="a3e88-110">Use this dialog box to understand the dependencies before changing or deleting the selected object.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="a3e88-111">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="a3e88-111">UI element list</span></span>  
 <span data-ttu-id="a3e88-112">**に依存するオブジェクト**  _\<selected object>_</span><span class="sxs-lookup"><span data-stu-id="a3e88-112">**Objects that depend on**  _\<selected object>_</span></span>  
 <span data-ttu-id="a3e88-113">このボタンをクリックすると、依存関係が監視され、選択されているオブジェクトに依存するオブジェクトの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3e88-113">Clicking this button displays a list of those objects that are dependency-tracked and that depend on the selected object.</span></span>  
  
 <span data-ttu-id="a3e88-114">**オブジェクト** _\<selected object>_**依存**    </span><span class="sxs-lookup"><span data-stu-id="a3e88-114">**Objects on which**  _\<selected object>_  **depends**</span></span>  
 <span data-ttu-id="a3e88-115">このボタンをクリックすると、依存関係が監視され、選択されているオブジェクトが依存するオブジェクトの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3e88-115">Clicking this button displays a list of those objects that are dependency-tracked, on which the selected object depends.</span></span>  
  
 <span data-ttu-id="a3e88-116">**依存関係**</span><span class="sxs-lookup"><span data-stu-id="a3e88-116">**Dependencies**</span></span>  
 <span data-ttu-id="a3e88-117">**[** _\<selected object> に依存するオブジェクト]_ をクリックした場合は、選択されているオブジェクトに依存するオブジェクトの階層ビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3e88-117">If **Objects that depend on** _\<selected object>_ is clicked, this displays an hierarchical view of objects that depend on the selected object.</span></span> <span data-ttu-id="a3e88-118">**[** _\<selected object>_ **が依存するオブジェクト]** をクリックすると、選択されているオブジェクトが依存するオブジェクトの階層ビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3e88-118">If **Objects on which** _\<selected object>_ **depends** is clicked, this displays an hierarchical view of objects on which the selected object depends.</span></span>  
  
 <span data-ttu-id="a3e88-119">**Name**</span><span class="sxs-lookup"><span data-stu-id="a3e88-119">**Name**</span></span>  
 <span data-ttu-id="a3e88-120">上記の **[依存関係]** ツリー ビューで選択されたオブジェクトの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3e88-120">Displays the name of the object selected in the **Dependencies** tree view above.</span></span>  
  
 <span data-ttu-id="a3e88-121">**Type**</span><span class="sxs-lookup"><span data-stu-id="a3e88-121">**Type**</span></span>  
 <span data-ttu-id="a3e88-122">上記の **[依存関係]** ツリー ビューで選択されたオブジェクトの種類が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3e88-122">Displays the type of the object selected in the **Dependencies** tree view above.</span></span>  
  
 <span data-ttu-id="a3e88-123">**[最終同期時刻]**</span><span class="sxs-lookup"><span data-stu-id="a3e88-123">**Last Sync Time**</span></span>  
 > [!NOTE]  
>  <span data-ttu-id="a3e88-124">このオプションは、 **[詳細設定]** ページのみで使用できます。</span><span class="sxs-lookup"><span data-stu-id="a3e88-124">This option is available only on the **Advanced** page.</span></span>  
  
 <span data-ttu-id="a3e88-125">依存関係情報が最後に更新された日時を指定します。</span><span class="sxs-lookup"><span data-stu-id="a3e88-125">Specifies the time and date when the dependency information was last updated.</span></span>  
  
 <span data-ttu-id="a3e88-126">**[依存関係の種類]**</span><span class="sxs-lookup"><span data-stu-id="a3e88-126">**Dependency type**</span></span>  
 > [!NOTE]  
>  <span data-ttu-id="a3e88-127">このオプションは、 **[全般]** ページのみで使用できます。</span><span class="sxs-lookup"><span data-stu-id="a3e88-127">This option is available only on the **General** page.</span></span>  
  
 <span data-ttu-id="a3e88-128">2 つのオブジェクト間の依存関係の種類が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3e88-128">Displays the type of dependency between two objects.</span></span> <span data-ttu-id="a3e88-129">以下のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a3e88-129">Can be one of the following:</span></span>  
  
-   <span data-ttu-id="a3e88-130">スキーマ バインド依存関係</span><span class="sxs-lookup"><span data-stu-id="a3e88-130">Schema-bound dependency</span></span>  
  
     <span data-ttu-id="a3e88-131">参照元オブジェクトが存在する限り、参照先オブジェクトを削除または変更することができない 2 つのオブジェクト間のリレーションシップです。</span><span class="sxs-lookup"><span data-stu-id="a3e88-131">Is a relationship between two objects that prevents the referenced object from being dropped or modified as long as the referencing object exists.</span></span> <span data-ttu-id="a3e88-132">スキーマ バインド依存関係は、WITH SCHEMABINDING 句を使用してビューまたはユーザー定義の関数を作成した場合か、テーブルが CHECK 制約または DEFAULT 制約を通じてあるいは計算列の定義で別のオブジェクトを参照している場合に作成されます。</span><span class="sxs-lookup"><span data-stu-id="a3e88-132">A schema-bound dependency is created when a view or user-defined function is created by using the WITH SCHEMABINDING clause, or when a table references another object through a CHECK or DEFAULT constraint or in the definition of a computed column.</span></span>  
  
-   <span data-ttu-id="a3e88-133">非スキーマ バインド依存関係</span><span class="sxs-lookup"><span data-stu-id="a3e88-133">Non-schema-bound dependency</span></span>  
  
     <span data-ttu-id="a3e88-134">参照先オブジェクトを削除または変更できる 2 つのオブジェクト間のリレーションシップです。</span><span class="sxs-lookup"><span data-stu-id="a3e88-134">Is a relationship between two objects that does not prevent the referenced object from being dropped or modified.</span></span>  
  
-   <span data-ttu-id="a3e88-135">使用不可または未解決のエンティティ</span><span class="sxs-lookup"><span data-stu-id="a3e88-135">Not available or Unresolved Entity</span></span>  
  
     <span data-ttu-id="a3e88-136">依存関係の種類を判断できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="a3e88-136">Indicates the dependency type cannot be determined.</span></span> <span data-ttu-id="a3e88-137">これは、選択したオブジェクトが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] よりも前 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]のインスタンスである場合にのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="a3e88-137">This occurs only when the selected object is on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
  
