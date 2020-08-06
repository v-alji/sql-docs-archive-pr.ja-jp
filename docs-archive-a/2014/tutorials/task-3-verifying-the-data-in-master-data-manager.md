---
title: 'タスク 3: マスターデータマネージャー | でデータを検証するMicrosoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: d88953d2-2258-40ac-b3bf-2ef502f9b5fd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: aed5a76cff9d90b81f02f6af11b6fc437efee14e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632837"
---
# <a name="task-3-verifying-the-data-in-master-data-manager"></a><span data-ttu-id="49a83-102">タスク 3: マスター データ マネージャーのデータを確認する</span><span class="sxs-lookup"><span data-stu-id="49a83-102">Task 3: Verifying the Data in Master Data Manager</span></span>
  <span data-ttu-id="49a83-103">このタスクでは、**マスターデータマネージャー Web アプリケーション**を使用して、 **Supplier で Supplier**エンティティが作成さ**れている**ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="49a83-103">In this task, you verify that the **Supplier** entity is created on **MDS** using **Master Data Manager Web Application**.</span></span>

1.  <span data-ttu-id="49a83-104">**マスターデータマネージャー**が既に開いている場合は、上部にある**SQL Server 2012 マスターデータサービス**をクリックして、ホームページに移動します。</span><span class="sxs-lookup"><span data-stu-id="49a83-104">If **Master Data Manager** is already open, click **SQL Server 2012 Master Data Services** at the top to navigate to the home page.</span></span> <span data-ttu-id="49a83-105">それ以外の場合は、に移動して `http://localhost/MDS` **マスターデータマネージャー**を起動します。</span><span class="sxs-lookup"><span data-stu-id="49a83-105">Otherwise, navigate to `http://localhost/MDS` to launch **Master Data Manager**.</span></span>

2.  <span data-ttu-id="49a83-106">[**モデル**] で [**仕入先**] を選択し、[**エクスプローラー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="49a83-106">Select **Suppliers** for **Model**, and click **Explorer**.</span></span>

     <span data-ttu-id="49a83-107">![マスター データ マネージャー - [エクスプローラー] ボタン](../../2014/tutorials/media/et-verifyingthedatainmasterdatamanager.jpg "マスター データ マネージャー - [エクスプローラー] ボタン")</span><span class="sxs-lookup"><span data-stu-id="49a83-107">![Master Data Manager - Explorer Button](../../2014/tutorials/media/et-verifyingthedatainmasterdatamanager.jpg "Master Data Manager - Explorer Button")</span></span>

3.  <span data-ttu-id="49a83-108">MDS に格納されているデータを確認します。</span><span class="sxs-lookup"><span data-stu-id="49a83-108">Review the data stored on MDS.</span></span> <span data-ttu-id="49a83-109">データが表示されない場合は、**エクスプローラー**を起動する前に、ホームページで**モデル**の [**仕入先**] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="49a83-109">If you do not see the data, confirm that you selected **Suppliers** for the **Model** on the home page before launching **Explorer**.</span></span> <span data-ttu-id="49a83-110">ツールバーの [**メンバーの追加**] および [**メンバーの削除**] ボタンを使用して、仕入先の一覧に対して追加または削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="49a83-110">You can add to or delete from the supplier list by using **Add Member** and **Delete Member** buttons on the toolbar.</span></span>

## <a name="next-step"></a><span data-ttu-id="49a83-111">次の手順</span><span class="sxs-lookup"><span data-stu-id="49a83-111">Next Step</span></span>
 [<span data-ttu-id="49a83-112">タスク 4 &#40;オプションの&#41;: 新しいデータセットの結合、照合、およびパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="49a83-112">Task 4 &#40;Optional&#41;: Combining, Matching, and Publishing New Set of Data</span></span>](../../2014/tutorials/task-4-optional-combining-matching-and-publishing-new-set-of-data.md)


