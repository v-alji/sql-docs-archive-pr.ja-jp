---
title: パブリケーション データベース | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.publicationdatabase.f1
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 511e5f2e2caa934313ba96fb3dbc4cadddace968
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631806"
---
# <a name="publication-database"></a><span data-ttu-id="0ad52-102">パブリケーション データベース</span><span class="sxs-lookup"><span data-stu-id="0ad52-102">Publication Database</span></span>
  <span data-ttu-id="0ad52-103">パブリケーション データベースは、レプリケートされるデータおよびデータベース オブジェクトの供給元として機能する、パブリッシャー上のデータベースです。</span><span class="sxs-lookup"><span data-stu-id="0ad52-103">The publication database is the database on the Publisher that is the source of data and database objects to be replicated.</span></span> <span data-ttu-id="0ad52-104">レプリケーションに使用される各パブリケーション データベースは有効である必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ad52-104">Each publication database used in replication must be enabled.</span></span> <span data-ttu-id="0ad52-105">データベースは、 **sysadmin** 固定サーバー ロールのメンバーが次のことを行う場合に有効です。</span><span class="sxs-lookup"><span data-stu-id="0ad52-105">The database is enabled when a member of the **sysadmin** fixed server role:</span></span>  
  
-   <span data-ttu-id="0ad52-106">パブリケーションの新規作成ウィザードを使用してデータベースにパブリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="0ad52-106">Creates a publication on that database using the New Publication Wizard.</span></span>  
  
-   <span data-ttu-id="0ad52-107">**[パブリッシャーのプロパティ]** ダイアログ ボックスでデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="0ad52-107">Selects the database in the **Publisher Properties** dialog box.</span></span>  
  
-   <span data-ttu-id="0ad52-108">**sp_replicationdboption** を実行し、オプションの **publish** (スナップショット用またはトランザクション パブリケーション用) または **merge publish** (マージ パブリケーション用) を **True**に設定します。</span><span class="sxs-lookup"><span data-stu-id="0ad52-108">Executes **sp_replicationdboption** and sets the option **publish** (for snapshot or transactional publications) or **merge publish** (for merge publications) to **True**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0ad52-109">オプション</span><span class="sxs-lookup"><span data-stu-id="0ad52-109">Options</span></span>  
 <span data-ttu-id="0ad52-110">**データベース**</span><span class="sxs-lookup"><span data-stu-id="0ad52-110">**Databases**</span></span>  
 <span data-ttu-id="0ad52-111">パブリッシュするデータおよびデータベース オブジェクトを含むデータベースの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="0ad52-111">Select the name of the database that contains the data and database objects that you want to publish.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ad52-112">参照</span><span class="sxs-lookup"><span data-stu-id="0ad52-112">See Also</span></span>  
 <span data-ttu-id="0ad52-113">[データとデータベース オブジェクトのパブリッシュ](publish/publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="0ad52-113">[Publish Data and Database Objects](publish/publish-data-and-database-objects.md) </span></span>  
 <span data-ttu-id="0ad52-114">[Create a Publication](publish/create-a-publication.md) </span><span class="sxs-lookup"><span data-stu-id="0ad52-114">[Create a Publication](publish/create-a-publication.md) </span></span>  
 <span data-ttu-id="0ad52-115">[View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](view-and-modify-distributor-and-publisher-properties.md) </span><span class="sxs-lookup"><span data-stu-id="0ad52-115">[View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md) </span></span>  
 [<span data-ttu-id="0ad52-116">sp_replicationdboption &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0ad52-116">sp_replicationdboption &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)  
  
  
