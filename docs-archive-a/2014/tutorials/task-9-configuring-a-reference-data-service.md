---
title: 'タスク 9: 参照データサービスを構成する |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: d0535fce-2bf5-4f6d-b517-ffe6fa13738d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1e7c685de13a2f5c495482f816818ff6b838fc7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742645"
---
# <a name="task-9-configuring-a-reference-data-service"></a><span data-ttu-id="1899f-102">タスク 9: 参照データ サービスを構成する</span><span class="sxs-lookup"><span data-stu-id="1899f-102">Task 9: Configuring a Reference Data Service</span></span>
  <span data-ttu-id="1899f-103">このタスクでは、Azure Marketplace で参照データサービスを使用するように DQS を構成します。</span><span class="sxs-lookup"><span data-stu-id="1899f-103">In this task, you configure DQS to use a Reference Data Service on Azure Marketplace.</span></span> <span data-ttu-id="1899f-104">次のタスクでは、このサービスを使用するように**アドレス検証**ドメインを構成します。</span><span class="sxs-lookup"><span data-stu-id="1899f-104">In the next task, you will configure the **Address Validation** domain to use this service.</span></span> <span data-ttu-id="1899f-105">実行時に、クレンジングアクティビティ中に、DQS は、クレンジングのために**アドレス検証**ドメインのドメインの値をサービスに渡します。</span><span class="sxs-lookup"><span data-stu-id="1899f-105">At runtime, during cleansing activity, DQS passes the values of domains in the **Address Validation** domain to the service for cleansing.</span></span> <span data-ttu-id="1899f-106">詳細については、「[参照データを使用するように DQS を構成する」を](https://msdn.microsoft.com/library/hh213070.aspx)参照してください。</span><span class="sxs-lookup"><span data-stu-id="1899f-106">See [Configure DQS to Use Reference Data](https://msdn.microsoft.com/library/hh213070.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="1899f-107">**DQS クライアント**のメインページの [**管理**] ウィンドウで、[**構成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1899f-107">In the main page of **DQS Client**, in the **Administration** pane, click **Configuration**.</span></span>  
  
2.  <span data-ttu-id="1899f-108">[**参照データ**] タブがアクティブであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1899f-108">Ensure that **Reference Data** tab is active.</span></span>  
  
3.  <span data-ttu-id="1899f-109">プロキシサーバーを使用してインターネットに接続する必要がある場合は、[**ネットワーク設定**] 領域で、[**プロキシサーバー** ] と [**ポート**] フィールドに適切な値を入力します。</span><span class="sxs-lookup"><span data-stu-id="1899f-109">In the **Network Settings** area, type appropriate values in the **Proxy Server** and **Port** fields if you need to use a proxy server to connect to Internet.</span></span>  
  
4.  <span data-ttu-id="1899f-110">[ **DataMarket のアカウント ID** ] フィールドに**Azure Marketplace アカウントキー**を入力します。</span><span class="sxs-lookup"><span data-stu-id="1899f-110">Type your **Azure Marketplace Account Key** for the **DataMarket Account ID** field.</span></span>  
  
     <span data-ttu-id="1899f-111">![Azure Data Market 参照データ サービス アカウント](../../2014/tutorials/media/et-configuringareferencedataservice.jpg "Azure Data Market 参照データ サービス アカウント")</span><span class="sxs-lookup"><span data-stu-id="1899f-111">![Azure Data Market Reference Data Service Account](../../2014/tutorials/media/et-configuringareferencedataservice.jpg "Azure Data Market Reference Data Service Account")</span></span>  
  
5.  <span data-ttu-id="1899f-112">アカウント ID を検証するには、テキストボックスの横にある [**検証**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1899f-112">Click **Validate** button next to the text box to validate the account ID.</span></span>  
  
6.  <span data-ttu-id="1899f-113">メッセージボックスで [ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1899f-113">Click **OK** on the message box.</span></span>  
  
7.  <span data-ttu-id="1899f-114">ページの下部にある [**閉じる**] をクリックして、DQS クライアントのメインページに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="1899f-114">Click **Close** at the bottom of the page to switch to the main page of DQS Client.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="1899f-115">次の作業</span><span class="sxs-lookup"><span data-stu-id="1899f-115">Next Task</span></span>  
 [<span data-ttu-id="1899f-116">タスク 10: 参照データ サービスを使用して複合ドメインを構成する</span><span class="sxs-lookup"><span data-stu-id="1899f-116">Task 10: Configuring Composite Domain to Use Reference Data Service</span></span>](../../2014/tutorials/task-10-configuring-composite-domain-to-use-reference-data-service.md)  
  
  
