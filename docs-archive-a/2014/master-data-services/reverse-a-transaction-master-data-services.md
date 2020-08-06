---
title: トランザクションを破棄する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Master Data Services], reversing
ms.assetid: 6f7c3f07-0f64-4283-8c9c-93facd00a046
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fb5b1b0932b65b1d6f8fe7b1bc842836e21aaca6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714450"
---
# <a name="reverse-a-transaction-master-data-services"></a><span data-ttu-id="b5948-102">トランザクションを破棄する (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b5948-102">Reverse a Transaction (Master Data Services)</span></span>
  <span data-ttu-id="b5948-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、管理者は、アクションを元に戻す必要があるときにトランザクションを破棄できます。</span><span class="sxs-lookup"><span data-stu-id="b5948-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], administrators can reverse a transaction when an action needs to be undone.</span></span> <span data-ttu-id="b5948-104">トランザクションの例としては、属性値の変更、階層の移動、メンバーの削除などがあります。</span><span class="sxs-lookup"><span data-stu-id="b5948-104">Examples of transactions are attribute value changes, hierarchy moves, or member deletions.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b5948-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="b5948-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="b5948-106">**[バージョン管理]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="b5948-106">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="b5948-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5948-107">You must be a model administrator.</span></span> <span data-ttu-id="b5948-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5948-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-reverse-a-transaction"></a><span data-ttu-id="b5948-109">トランザクションを破棄するには</span><span class="sxs-lookup"><span data-stu-id="b5948-109">To reverse a transaction</span></span>  
  
1.  <span data-ttu-id="b5948-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ホーム ページで、 **[バージョン管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5948-110">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="b5948-111">メニュー バーの **[トランザクション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5948-111">On the menu bar, click **Transactions**.</span></span>  
  
3.  <span data-ttu-id="b5948-112">**[トランザクション]** ページで、 **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b5948-112">On the **Transactions** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="b5948-113">**[バージョン]** ボックスの一覧からバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="b5948-113">From the **Version** list, select a version.</span></span>  
  
5.  <span data-ttu-id="b5948-114">破棄するトランザクションのグリッド内の行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5948-114">Click the row in the grid for the transaction you want to reverse.</span></span>  
  
6.  <span data-ttu-id="b5948-115">**[トランザクションの破棄]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5948-115">Click **Reverse Transaction**.</span></span>  
  
7.  <span data-ttu-id="b5948-116">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5948-116">In the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="b5948-117">破棄されたトランザクションを記録するために、別のトランザクションがグリッドに追加されます。</span><span class="sxs-lookup"><span data-stu-id="b5948-117">Another transaction is added to the grid to record the reversed transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5948-118">参照</span><span class="sxs-lookup"><span data-stu-id="b5948-118">See Also</span></span>  
 <span data-ttu-id="b5948-119">[トランザクション &#40;マスターデータサービス&#41;](../../2014/master-data-services/transactions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="b5948-119">[Transactions &#40;Master Data Services&#41;](../../2014/master-data-services/transactions-master-data-services.md) </span></span>  
 [<span data-ttu-id="b5948-120">メンバーまたはコレクションを再アクティブ化する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b5948-120">Reactivate a Member or Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md)  
  
  
