---
title: 'タスク 1: マスターデータマネージャー | を使用してサプライヤーモデルを作成するMicrosoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6bbbcbff-1ecd-456c-947f-c445c8da673c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f6823c96acb7db77a3daafa895f3353b70af44dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714910"
---
# <a name="task-1-creating-suppliers-model-using-master-data-manager"></a><span data-ttu-id="7270c-102">タスク 1: マスター データ マネージャーを使用して Suppliers モデルを作成する</span><span class="sxs-lookup"><span data-stu-id="7270c-102">Task 1: Creating Suppliers Model using Master Data Manager</span></span>
  <span data-ttu-id="7270c-103">このタスクでは、**マスターデータマネージャー**を使用して、MDS で**仕入先**という名前のモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7270c-103">In this task, you create a model named **Suppliers** in MDS using **Master Data Manager**.</span></span>  
  
1.  <span data-ttu-id="7270c-104">に移動して `http://localhost/MDS` **マスターデータマネージャー**を起動します。</span><span class="sxs-lookup"><span data-stu-id="7270c-104">Navigate to `http://localhost/MDS` to launch **Master Data Manager**.</span></span> <span data-ttu-id="7270c-105">別の名前または別の Web サイトで Web アプリケーションを構成した場合は、URL を置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="7270c-105">Replace the URL if you have configured Web Application with a different name or on a different a web site.</span></span>  
  
     <span data-ttu-id="7270c-106">![マスター データ マネージャー - システム管理](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-01.jpg "マスター データ マネージャー - システム管理")</span><span class="sxs-lookup"><span data-stu-id="7270c-106">![Master Data Manager - System Administation](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-01.jpg "Master Data Manager - System Administation")</span></span>  
  
2.  <span data-ttu-id="7270c-107">[**管理タスク**] セクションで [**システム管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7270c-107">Click **System Administration** in the **Administrative Tasks** section.</span></span>  
  
3.  <span data-ttu-id="7270c-108">[**モデルの追加**] ページが表示されない場合は、メニューバーの [**管理**] の上にマウスポインターを移動し、[**モデル**] をクリックします。次に、[モデルの**追加] (+)** ツールバーボタンをクリックしてモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7270c-108">If you do not see the **Add Model** page, hover mouse over **Manage** on the menu bar, click **Models**, and then click **Add Model (+)** toolbar button to create a model.</span></span>  
  
     <span data-ttu-id="7270c-109">![管理 - [モデル] メニュー](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-02.jpg "管理 - [モデル] メニュー")</span><span class="sxs-lookup"><span data-stu-id="7270c-109">![Manage - Models Menu](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-02.jpg "Manage - Models Menu")</span></span>  
  
     <span data-ttu-id="7270c-110">![[モデルの追加] ツール バー ボタン](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-03.jpg "[モデルの追加] ツール バー ボタン")</span><span class="sxs-lookup"><span data-stu-id="7270c-110">![Add Model Toolbat Button](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-03.jpg "Add Model Toolbat Button")</span></span>  
  
4.  <span data-ttu-id="7270c-111">**モデル名**として「**仕入先**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="7270c-111">Enter **Suppliers** for **Model name**.</span></span>  
  
5.  <span data-ttu-id="7270c-112">[**モデルと同じ名前のエンティティを作成する**] オプションをオフにします。</span><span class="sxs-lookup"><span data-stu-id="7270c-112">Clear **Create entity with same name as model** option.</span></span> <span data-ttu-id="7270c-113">エンティティを作成するには、後で**Excel 用 MDS アドイン**を使用します。</span><span class="sxs-lookup"><span data-stu-id="7270c-113">You will create an entity later using the **MDS Add-in for Excel**.</span></span>  
  
     <span data-ttu-id="7270c-114">![[モデルの追加] ページ](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-04.jpg "[モデルの追加] ページ")</span><span class="sxs-lookup"><span data-stu-id="7270c-114">![Add Model Page](../../2014/tutorials/media/et-creatingsuppliersmodelusingmdm-04.jpg "Add Model Page")</span></span>  
  
6.  <span data-ttu-id="7270c-115">ツールバーの [**モデルの保存**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7270c-115">Click **Save Model** button on the toolbar.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="7270c-116">次の手順</span><span class="sxs-lookup"><span data-stu-id="7270c-116">Next Step</span></span>  
 [<span data-ttu-id="7270c-117">タスク 2: Excel 用 MDS アドインを使用して仕入先データを MDS にアップロードする</span><span class="sxs-lookup"><span data-stu-id="7270c-117">Task 2: Uploading Supplier Data to MDS using MDS Add-in for Excel</span></span>](../../2014/tutorials/task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel.md)  
  
  
