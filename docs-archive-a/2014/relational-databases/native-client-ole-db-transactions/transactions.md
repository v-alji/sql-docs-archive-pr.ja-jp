---
title: トランザクション | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: 3b41e33a-c1ca-4b2a-9464-312b0ed3ca89
author: rothja
ms.author: jroth
ms.openlocfilehash: 1067820e80f9c7a4e1af2c8a14c85bc9dbfdd6aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643785"
---
# <a name="transactions"></a><span data-ttu-id="aa0bf-102">トランザクション</span><span class="sxs-lookup"><span data-stu-id="aa0bf-102">Transactions</span></span>
  <span data-ttu-id="aa0bf-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、ローカルトランザクションサポートを実装します。</span><span class="sxs-lookup"><span data-stu-id="aa0bf-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements local transaction support.</span></span> <span data-ttu-id="aa0bf-104">コンシューマーは、MS DTC (Microsoft 分散トランザクション コーディネーター) を使用して、分散トランザクションまたはコーディネートされたトランザクションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="aa0bf-104">The consumer can use distributed or coordinated transactions by using Microsoft Distributed Transaction Coordinator (MS DTC).</span></span> <span data-ttu-id="aa0bf-105">複数のセッションにまたがるトランザクション制御を必要とするコンシューマーの場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは MS DTC によって開始および管理されるトランザクションに参加できます。</span><span class="sxs-lookup"><span data-stu-id="aa0bf-105">For consumers requiring transaction control that spans multiple sessions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider can join transactions initiated and maintained by MS DTC.</span></span>  
  
 <span data-ttu-id="aa0bf-106">既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは自動コミットトランザクションモードを使用します。このモードでは、コンシューマーセッションの各個別アクションがのインスタンスに対する完全なトランザクションで構成さ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] れます。</span><span class="sxs-lookup"><span data-stu-id="aa0bf-106">By default, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider uses an autocommit transaction mode, where each discrete action on a consumer session comprises a complete transaction against an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="aa0bf-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーの自動コミットモードはローカルであり、自動コミットトランザクションが1つ以上のセッションにまたがることはありません。</span><span class="sxs-lookup"><span data-stu-id="aa0bf-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider autocommit mode is local, and autocommit transactions never span more than a single session.</span></span>  
  
 <span data-ttu-id="aa0bf-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 **ITransactionLocal**インターフェイスを公開します。これにより、コンシューマーは、のインスタンスへの1つの接続で、明示的かつ暗黙的にトランザクションを開始でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="aa0bf-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ITransactionLocal** interface, allowing the consumer to use explicitly and implicitly start transactions on a single connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="aa0bf-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、入れ子になったローカルトランザクションをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="aa0bf-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support nested local transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aa0bf-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="aa0bf-110">In This Section</span></span>  
  
-   [<span data-ttu-id="aa0bf-111">ローカル トランザクションのサポート</span><span class="sxs-lookup"><span data-stu-id="aa0bf-111">Supporting Local Transactions</span></span>](supporting-local-transactions.md)  
  
-   [<span data-ttu-id="aa0bf-112">分散トランザクションのサポート</span><span class="sxs-lookup"><span data-stu-id="aa0bf-112">Supporting Distributed Transactions</span></span>](supporting-distributed-transactions.md)  
  
-   [<span data-ttu-id="aa0bf-113">分離レベル &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="aa0bf-113">Isolation Levels &#40;OLE DB&#41;</span></span>](isolation-levels-ole-db.md)  
  
## <a name="see-also"></a><span data-ttu-id="aa0bf-114">参照</span><span class="sxs-lookup"><span data-stu-id="aa0bf-114">See Also</span></span>  
 [<span data-ttu-id="aa0bf-115">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="aa0bf-115">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
