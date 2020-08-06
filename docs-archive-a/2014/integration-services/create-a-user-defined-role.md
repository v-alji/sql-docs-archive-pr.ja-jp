---
title: ユーザー定義のロールを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c4128993-2333-48c7-84b1-e51cdcea393d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a0ee905c2636e20315c2180a6be8f8e40f76d5f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639575"
---
# <a name="create-a-user-defined-role"></a><span data-ttu-id="b9c67-102">ユーザー定義ロールを作成する</span><span class="sxs-lookup"><span data-stu-id="b9c67-102">Create a User-Defined Role</span></span>
    
### <a name="to-create-a-user-defined-role"></a><span data-ttu-id="b9c67-103">ユーザー定義ロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="b9c67-103">To create a user-defined role</span></span>  
  
1.  <span data-ttu-id="b9c67-104">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を開きます。</span><span class="sxs-lookup"><span data-stu-id="b9c67-104">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="b9c67-105">**[表示]** メニューの **[オブジェクト エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9c67-105">Click **Object Explorer** on the **View** menu.</span></span>  
  
3.  <span data-ttu-id="b9c67-106">オブジェクト エクスプローラー ツール バーで **[接続]** をクリックし、 **[データベース エンジン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9c67-106">On the Object Explorer toolbar, click **Connect**, and then click **Database Engine**.</span></span>  
  
4.  <span data-ttu-id="b9c67-107">**[サーバーへの接続]** ダイアログ ボックスで、サーバー名を指定し、認証モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="b9c67-107">In the **Connect to Server** dialog box, provide a server name and select an authentication mode.</span></span> <span data-ttu-id="b9c67-108">ピリオド (.)、(local)、または `localhost` を使用すると、ローカル サーバーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b9c67-108">You can use a period (.), (local), or `localhost` to indicate the local server.</span></span>  
  
5.  <span data-ttu-id="b9c67-109">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9c67-109">Click **Connect**.</span></span>  
  
6.  <span data-ttu-id="b9c67-110">[データベース]、[システム データベース]、[msdb]、[セキュリティ]、[ロール] を順に展開します。</span><span class="sxs-lookup"><span data-stu-id="b9c67-110">Expand Databases, System Databases, msdb, Security, and Roles.</span></span>  
  
7.  <span data-ttu-id="b9c67-111">[ロール] ノードの [データベース ロール] を右クリックし、 **[新しいデータベース ロール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9c67-111">In the Roles node, right-click Database Roles, and click **New Database Role**.</span></span>  
  
8.  <span data-ttu-id="b9c67-112">[全般] ページでロール名を指定します。必要に応じて、所有者および所有されているスキーマを指定し、ロール メンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="b9c67-112">On the General page, provide a name and optionally, specify an owner and owned schemas and add role members.</span></span>  
  
9. <span data-ttu-id="b9c67-113">必要に応じて、 **[権限]** をクリックし、オブジェクトの権限を構成します。</span><span class="sxs-lookup"><span data-stu-id="b9c67-113">Optionally, click **Permissions** and configure object permissions.</span></span>  
  
10. <span data-ttu-id="b9c67-114">必要に応じて、 **[拡張プロパティ]** をクリックし、任意の拡張プロパティを構成します。</span><span class="sxs-lookup"><span data-stu-id="b9c67-114">Optionally, click **Extended Properties** and configure any extended properties.</span></span>  
  
11. <span data-ttu-id="b9c67-115">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9c67-115">Click **OK**.</span></span>  
  
  
