---
title: パブリケーションのアーティクルの追加および削除 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], dropping
- deleting articles
- dropping articles
- adding articles
- articles [SQL Server replication], adding
ms.assetid: d5a3e536-62d2-4473-a178-877ba52f7d7f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f7af1cac1f3ee8ecc9cb79632f8a4ef1e66ec82f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645530"
---
# <a name="add-articles-to-and-drop-articles-from-a-publication-sql-server-management-studio"></a><span data-ttu-id="8efba-102">パブリケーションでのアーティクルの追加または削除 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="8efba-102">Add Articles to and Drop Articles from a Publication (SQL Server Management Studio)</span></span>
  <span data-ttu-id="8efba-103">パブリケーションの新規作成ウィザードでパブリケーションを作成する場合は、最初にアーティクルを追加します。</span><span class="sxs-lookup"><span data-stu-id="8efba-103">Initially add articles to a publication when you create it in the New Publication Wizard.</span></span> <span data-ttu-id="8efba-104">このウィザードの使用の詳細については、「[パブリケーションの作成](create-a-publication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8efba-104">For more information about using this wizard, see [Create a Publication](create-a-publication.md).</span></span>  
  
 <span data-ttu-id="8efba-105">パブリケーションの作成後、 **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[アーティクル]** ページでアーティクルを追加または削除します。</span><span class="sxs-lookup"><span data-stu-id="8efba-105">After a publication is created, add and delete articles on the **Articles** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="8efba-106">このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](view-and-modify-publication-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8efba-106">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span> <span data-ttu-id="8efba-107">アーティクルの追加と削除に関する注意点については、「[既存のパブリケーションでのアーティクルの追加および削除](add-articles-to-and-drop-articles-from-existing-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8efba-107">For information about the considerations for adding and dropping articles, see [Add Articles to and Drop Articles from Existing Publications](add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
### <a name="to-add-an-article-after-a-publication-is-created"></a><span data-ttu-id="8efba-108">パブリケーションの作成後にアーティクルを追加するには</span><span class="sxs-lookup"><span data-stu-id="8efba-108">To add an article after a publication is created</span></span>  
  
1.  <span data-ttu-id="8efba-109">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[アーティクル]** ページで、 **[チェック ボックスがオンのオブジェクトのみ一覧に表示する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="8efba-109">On the **Articles** page of the **Publication Properties - \<Publication>** dialog box, clear the **Show only checked objects in the list** check box.</span></span> <span data-ttu-id="8efba-110">これにより、パブリケーション データベース内のパブリッシュされていないオブジェクトも表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="8efba-110">This allows you to see the unpublished objects in the publication database.</span></span>  
  
2.  <span data-ttu-id="8efba-111">追加する各アーティクルの隣にあるチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="8efba-111">Select the check box next to each article you want to add.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-delete-an-article"></a><span data-ttu-id="8efba-112">アーティクルを削除するには</span><span class="sxs-lookup"><span data-stu-id="8efba-112">To delete an article</span></span>  
  
1.  <span data-ttu-id="8efba-113">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[アーティクル]** ページで、削除するアーティクルの隣にあるチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="8efba-113">On the **Articles** page of the **Publication Properties - \<Publication>** dialog box, clear the check box next to each article you want to delete.</span></span>  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8efba-114">参照</span><span class="sxs-lookup"><span data-stu-id="8efba-114">See Also</span></span>  
 <span data-ttu-id="8efba-115">[Define an Article](define-an-article.md) </span><span class="sxs-lookup"><span data-stu-id="8efba-115">[Define an Article](define-an-article.md) </span></span>  
 [<span data-ttu-id="8efba-116">データとデータベース オブジェクトのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="8efba-116">Publish Data and Database Objects</span></span>](publish-data-and-database-objects.md)  
  
  
