---
title: 「データベースのプロパティ」 ([ファイル] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.files.f1
ms.assetid: 3c030e51-db82-4b43-b1e5-8547ddd3de87
author: stevestein
ms.author: sstein
ms.openlocfilehash: 955a17857ce0d847fb712473dddd581a072ab83d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712021"
---
# <a name="database-properties-files-page"></a><span data-ttu-id="96a6d-102">「データベースのプロパティ」 ([ファイル] ページ)</span><span class="sxs-lookup"><span data-stu-id="96a6d-102">Database Properties (Files Page)</span></span>
  <span data-ttu-id="96a6d-103">このページを使用すると、新しいデータベースを作成したり、選択したデータベースのプロパティを表示または変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="96a6d-103">Use this page to create a new database, or view or modify properties for the selected database.</span></span> <span data-ttu-id="96a6d-104">このトピックは、既存のデータベースの **[データベースのプロパティ] ([ファイル] ページ)** 、および **[新しいデータベース] ([全般] ページ)** に該当します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-104">This topic applies to the **Database Properties (Files Page)** for existing databases, and to the **New Database (General Page)**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="96a6d-105">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="96a6d-105">UI element list</span></span>  
 <span data-ttu-id="96a6d-106">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="96a6d-106">**Database name**</span></span>  
 <span data-ttu-id="96a6d-107">データベースの名前を追加または表示します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-107">Add or display the name of the database.</span></span>  
  
 <span data-ttu-id="96a6d-108">**所有者**</span><span class="sxs-lookup"><span data-stu-id="96a6d-108">**Owner**</span></span>  
 <span data-ttu-id="96a6d-109">データベースの所有者を一覧から選択して指定します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-109">Specify the owner of the database by selecting from the list.</span></span>  
  
 <span data-ttu-id="96a6d-110">**フルテキスト インデックスを使用する**</span><span class="sxs-lookup"><span data-stu-id="96a6d-110">**Use full-text indexing**</span></span>  
 <span data-ttu-id="96a6d-111">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]ではフルテキスト インデックスが常に有効になっているため、このチェック ボックスはオンに設定され、変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="96a6d-111">This check box is checked and disabled because full-text indexing is always enabled in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="96a6d-112">詳細については、「 [フルテキスト検索](../search/full-text-search.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96a6d-112">For more information, see [Full-Text Search](../search/full-text-search.md).</span></span>  
  
 <span data-ttu-id="96a6d-113">**データベース ファイル**</span><span class="sxs-lookup"><span data-stu-id="96a6d-113">**Database Files**</span></span>  
 <span data-ttu-id="96a6d-114">関連付けられたデータベースのデータベース ファイルを追加、表示、変更、または削除します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-114">Add, view, modify, or remove database files for the associated database.</span></span> <span data-ttu-id="96a6d-115">データベース ファイルには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="96a6d-115">Database files have the following properties:</span></span>  
  
 <span data-ttu-id="96a6d-116">**[論理名]**</span><span class="sxs-lookup"><span data-stu-id="96a6d-116">**Logical Name**</span></span>  
 <span data-ttu-id="96a6d-117">ファイルの名前を入力または変更します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-117">Enter or modify the name of the file.</span></span>  
  
 <span data-ttu-id="96a6d-118">**[ファイルの種類]**</span><span class="sxs-lookup"><span data-stu-id="96a6d-118">**File Type**</span></span>  
 <span data-ttu-id="96a6d-119">ファイルの種類を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-119">Select the file type from the list.</span></span> <span data-ttu-id="96a6d-120">ファイルの種類は、 **データ**、 **ログ**、 **Filestream データ**のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="96a6d-120">The file type can be **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="96a6d-121">既存のファイルの種類は変更できません。</span><span class="sxs-lookup"><span data-stu-id="96a6d-121">You cannot modify the file type of an existing file.</span></span>  
  
 <span data-ttu-id="96a6d-122">メモリ最適化ファイル グループにファイル (コンテナー) を追加する場合は、 **FILESTREAM データ** を選択します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-122">Select **Filestream Data** if you are adding files (containers) to a memory-optimized filegroup.</span></span>  
  
 <span data-ttu-id="96a6d-123">FILESTREAM データ ファイル グループにファイル (コンテナー) を追加するには、FILESTREAM を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="96a6d-123">To add files (containers) to a Filestream data filegroup, FILESTREAM must be enabled.</span></span> <span data-ttu-id="96a6d-124">FILESTREAM を有効にするには、 [[サーバーのプロパティ] ([詳細設定] ページ)](../../database-engine/configure-windows/server-properties-advanced-page.md) ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-124">You can enable FILESTREAM by using the [Server Properties (Advanced Page)](../../database-engine/configure-windows/server-properties-advanced-page.md) dialog box.</span></span>  
  
 <span data-ttu-id="96a6d-125">**[ファイル グループ]**</span><span class="sxs-lookup"><span data-stu-id="96a6d-125">**Filegroup**</span></span>  
 <span data-ttu-id="96a6d-126">ファイルのファイル グループを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-126">Select the filegroup for the file from the list.</span></span> <span data-ttu-id="96a6d-127">既定のファイル グループは PRIMARY です。</span><span class="sxs-lookup"><span data-stu-id="96a6d-127">By default, the filegroup is PRIMARY.</span></span> <span data-ttu-id="96a6d-128">新しいファイル グループを作成するには、 **\<new filegroup>** を選択し、ファイル グループに関する情報を **[新しいファイル グループ]** ダイアログ ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-128">You can create a new filegroup by selecting **\<new filegroup>** and entering information about the filegroup in the **New Filegroup** dialog box.</span></span> <span data-ttu-id="96a6d-129">また、 **[ファイル グループ]** ページで新しいファイル グループを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="96a6d-129">A new filegroup can also be created on the **Filegroup** page.</span></span> <span data-ttu-id="96a6d-130">既存のファイルのファイル グループは変更できません。</span><span class="sxs-lookup"><span data-stu-id="96a6d-130">You cannot modify the filegroup of an existing file.</span></span>  
  
 <span data-ttu-id="96a6d-131">メモリ最適化ファイル グループにファイル (コンテナー) を追加すると、データベースのメモリ最適化ファイル グループ名が **[ファイル グループ]** フィールドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="96a6d-131">When adding files (containers) to a memory-optimized filegroup, the **Filegroup** field will be populated with the name of the database's memory-optimized filegroup.</span></span>  
  
 <span data-ttu-id="96a6d-132">**[初期サイズ]**</span><span class="sxs-lookup"><span data-stu-id="96a6d-132">**Initial Size**</span></span>  
 <span data-ttu-id="96a6d-133">ファイルの初期サイズをメガバイト単位で入力または変更します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-133">Enter or modify the initial size for the file in megabytes.</span></span> <span data-ttu-id="96a6d-134">既定値は **[モデル]** データベースの値となります。</span><span class="sxs-lookup"><span data-stu-id="96a6d-134">By default, this is the value of the **model** database.</span></span>  
  
 <span data-ttu-id="96a6d-135">FILESTREAM ファイルの場合、このフィールドは無効です。</span><span class="sxs-lookup"><span data-stu-id="96a6d-135">This field is not valid for FILESTREAM files.</span></span>  
  
 <span data-ttu-id="96a6d-136">メモリ最適化ファイル グループのファイルの場合、このフィールドは変更できません。</span><span class="sxs-lookup"><span data-stu-id="96a6d-136">For files in memory-optimized filegroups, this field cannot be modified.</span></span>  
  
 <span data-ttu-id="96a6d-137">**[自動拡張]**</span><span class="sxs-lookup"><span data-stu-id="96a6d-137">**Autogrowth**</span></span>  
 <span data-ttu-id="96a6d-138">ファイルの自動拡張プロパティを選択または表示します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-138">Select or display the autogrowth properties for the file.</span></span> <span data-ttu-id="96a6d-139">これらのプロパティは、ファイルが最大ファイル サイズに到達したときにファイルをどのように拡張するかを制御します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-139">These properties control how the file expands when its maximum file size is reached.</span></span> <span data-ttu-id="96a6d-140">自動拡張値を編集するには、目的のファイルの自動拡張プロパティの横にある編集ボタンをクリックし、 **[自動拡張の変更]** ダイアログ ボックスで値を変更します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-140">To edit autogrowth values, click the edit button next to the autogrowth properties for the file that you want, and change the values in the **Change Autogrowth** dialog box.</span></span> <span data-ttu-id="96a6d-141">既定値は **model** データベースの値となります。</span><span class="sxs-lookup"><span data-stu-id="96a6d-141">By default, these are the values of the **model** database.</span></span>  
  
 <span data-ttu-id="96a6d-142">FILESTREAM ファイルの場合、このフィールドは無効です。</span><span class="sxs-lookup"><span data-stu-id="96a6d-142">This field is not valid for FILESTREAM files.</span></span>  
  
 <span data-ttu-id="96a6d-143">メモリ最適化ファイル グループのファイルの場合、このフィールド **[無制限]** にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="96a6d-143">For files in memory-optimized filegroups, this field should be **Unlimited**.</span></span>  
  
 <span data-ttu-id="96a6d-144">**パス**</span><span class="sxs-lookup"><span data-stu-id="96a6d-144">**Path**</span></span>  
 <span data-ttu-id="96a6d-145">選択されているファイルのパスを表示します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-145">Displays the path of the selected file.</span></span> <span data-ttu-id="96a6d-146">新しいファイルのパスを指定するには、ファイルのパスの横にある編集ボタンをクリックし、目的のフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-146">To specify a path for a new file, click the edit button next to the path for the file, and navigate to the destination folder.</span></span> <span data-ttu-id="96a6d-147">既存のファイルのパスは変更できません。</span><span class="sxs-lookup"><span data-stu-id="96a6d-147">You cannot modify the path of an existing file.</span></span>  
  
 <span data-ttu-id="96a6d-148">FILESTREAM ファイルの場合、このパスはフォルダーになります。</span><span class="sxs-lookup"><span data-stu-id="96a6d-148">For FILESTREAM files, the path is a folder.</span></span> <span data-ttu-id="96a6d-149">このフォルダーには、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] によって基になるファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="96a6d-149">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] will create the underlying files in this folder.</span></span>  
  
 <span data-ttu-id="96a6d-150">**[ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="96a6d-150">**File Name**</span></span>  
 <span data-ttu-id="96a6d-151">ファイルの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-151">Displays the name of the file.</span></span>  
  
 <span data-ttu-id="96a6d-152">メモリ最適化ファイル グループのファイルを含めて、FILESTREAM ファイルの場合、このフィールドは無効です。</span><span class="sxs-lookup"><span data-stu-id="96a6d-152">This field is not valid for FILESTREAM files, including files in memory-optimized filegroups.</span></span>  
  
 <span data-ttu-id="96a6d-153">**追加**</span><span class="sxs-lookup"><span data-stu-id="96a6d-153">**Add**</span></span>  
 <span data-ttu-id="96a6d-154">データベースに新しいファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-154">Add a new file to the database.</span></span>  
  
 <span data-ttu-id="96a6d-155">**Remove**</span><span class="sxs-lookup"><span data-stu-id="96a6d-155">**Remove**</span></span>  
 <span data-ttu-id="96a6d-156">選択されているファイルをデータベースから削除します。</span><span class="sxs-lookup"><span data-stu-id="96a6d-156">Delete the selected file from the database.</span></span> <span data-ttu-id="96a6d-157">空でないファイルは削除できません。</span><span class="sxs-lookup"><span data-stu-id="96a6d-157">A file cannot be removed unless it is empty.</span></span> <span data-ttu-id="96a6d-158">プライマリ データ ファイルおよびログ ファイルは削除できません。</span><span class="sxs-lookup"><span data-stu-id="96a6d-158">The primary data file and log file cannot be removed.</span></span>  
  
 <span data-ttu-id="96a6d-159">ファイルの詳細については、「 [データベース ファイルとファイル グループ](database-files-and-filegroups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96a6d-159">For information about files, see [Database Files and Filegroups](database-files-and-filegroups.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96a6d-160">参照</span><span class="sxs-lookup"><span data-stu-id="96a6d-160">See Also</span></span>  
 <span data-ttu-id="96a6d-161">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="96a6d-161">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="96a6d-162">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="96a6d-162">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
