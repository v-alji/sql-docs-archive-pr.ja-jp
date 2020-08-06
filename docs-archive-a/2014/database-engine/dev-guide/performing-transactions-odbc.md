---
title: トランザクションの実行 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: f431191a-5762-4f0b-85bb-ac99aff29724
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8abc09c9395225dd653a072fd6c25dadce0849b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741237"
---
# <a name="performing-transactions-odbc"></a><span data-ttu-id="f3788-102">トランザクションの実行 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="f3788-102">Performing Transactions (ODBC)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f3788-103">と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、ODBC API トランザクションの管理関数がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f3788-103">and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver support the ODBC API transaction management functions.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="f3788-104">では、個別のサーバーでのローカル トランザクションの完全なサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="f3788-104">offers full support for local transactions on an individual server.</span></span> <span data-ttu-id="f3788-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、これらの機能を使用してトランザクションを管理する ODBC API 関数をサポートします。</span><span class="sxs-lookup"><span data-stu-id="f3788-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver uses these features to support the ODBC API functions that manage transactions.</span></span>  
  
 <span data-ttu-id="f3788-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、Microsoft 分散トランザクション コーディネーター (MS DTC) を使用して、複数のサーバーに展開された分散トランザクションに参加することができます。</span><span class="sxs-lookup"><span data-stu-id="f3788-106">Through the use of the Microsoft Distributed Transaction Coordinator (MS DTC), the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver can participate in distributed transactions spanning multiple servers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f3788-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f3788-107">In This Section</span></span>  
  
-   [<span data-ttu-id="f3788-108">ODBC でのトランザクション</span><span class="sxs-lookup"><span data-stu-id="f3788-108">Transactions in ODBC</span></span>](../../relational-databases/native-client/odbc/performing-transactions-in-odbc.md)  
  
-   [<span data-ttu-id="f3788-109">分散トランザクションの実行</span><span class="sxs-lookup"><span data-stu-id="f3788-109">Performing Distributed Transactions</span></span>](../../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  
