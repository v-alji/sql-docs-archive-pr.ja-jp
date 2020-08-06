---
title: SqlServerAlias クラス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- SqlServerAlias Class
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SqlServerAlias class
ms.assetid: 475662b9-6985-45bf-b1e9-b0f26ef50443
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 46994409cc6a5119c9144eb7a3a4b9a8a9a22c44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645432"
---
# <a name="sqlserveralias-class"></a><span data-ttu-id="506de-102">SqlServerAlias クラス</span><span class="sxs-lookup"><span data-stu-id="506de-102">SqlServerAlias Class</span></span>
  <span data-ttu-id="506de-103">[SqlServerAlias class](sqlserveralias-class.md)クラスは、サーバー接続の別名を表します。</span><span class="sxs-lookup"><span data-stu-id="506de-103">The [SqlServerAlias Class](sqlserveralias-class.md) class represents a server connection alias.</span></span>  
  
 <span data-ttu-id="506de-104">サーバー接続別名は、次の両方に該当する場合に必要となります。</span><span class="sxs-lookup"><span data-stu-id="506de-104">A server connection alias is required when both the following occur:</span></span>  
  
-   <span data-ttu-id="506de-105">クライアントが、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 既定のネットワーク転送ではないネットワークトランスポート経由でのインスタンスに接続しています。</span><span class="sxs-lookup"><span data-stu-id="506de-105">The client is connecting to an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] over a network transport that is not the default network transport.</span></span>  
  
-   <span data-ttu-id="506de-106">クライアントが接続されている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスが代替の名前付きパイプをリッスンする場合。</span><span class="sxs-lookup"><span data-stu-id="506de-106">The instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to which the client is connected listens on an alternate named pipe.</span></span>  
  
 <span data-ttu-id="506de-107">**注:**[SqlServerAlias クラス](sqlserveralias-class.md)は、 `Put` プロバイダークラスからメソッドを継承します。</span><span class="sxs-lookup"><span data-stu-id="506de-107">**Note:** The [SqlServerAlias Class](sqlserveralias-class.md) inherits the `Put` method from the Provider class.</span></span> <span data-ttu-id="506de-108">ただし、`Provider::Put` メソッドで示される結果は返されません。</span><span class="sxs-lookup"><span data-stu-id="506de-108">However, it does not return any results as indicated by the `Provider::Put` method.</span></span> <span data-ttu-id="506de-109">詳細については、WMI のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="506de-109">For more information, see the WMI documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="506de-110">参照</span><span class="sxs-lookup"><span data-stu-id="506de-110">See Also</span></span>  
 [<span data-ttu-id="506de-111">クライアント プロトコルの構成</span><span class="sxs-lookup"><span data-stu-id="506de-111">Configure Client Protocols</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
