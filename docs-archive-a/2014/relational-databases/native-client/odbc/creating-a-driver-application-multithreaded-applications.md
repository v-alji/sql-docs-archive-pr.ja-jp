---
title: マルチスレッドアプリケーション |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- threads [SQL Server], multithreaded applications
- ODBC applications, multithreaded applications
- asynchronous operations [SQL Server Native Client]
- SQL Server Native Client ODBC driver, multithreaded applications
- multithreaded applications [SQL Server Native Client]
ms.assetid: d352c91a-6e08-4e50-9f3e-a37892d9c2cc
author: rothja
ms.author: jroth
ms.openlocfilehash: b680086f76e0c1a1e8c8cfc2f4ef82099957b3fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643264"
---
# <a name="multithreaded-applications"></a><span data-ttu-id="bc708-102">マルチスレッド アプリケーション</span><span class="sxs-lookup"><span data-stu-id="bc708-102">Multithreaded Applications</span></span>
  <span data-ttu-id="bc708-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーはマルチスレッド ドライバーです。</span><span class="sxs-lookup"><span data-stu-id="bc708-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver is a multithreaded driver.</span></span> <span data-ttu-id="bc708-104">マルチスレッド アプリケーションは、非同期呼び出しを使用して複数の ODBC 呼び出しを処理するための代替手段として作成されます。</span><span class="sxs-lookup"><span data-stu-id="bc708-104">Writing a multithreaded application is an alternative to using asynchronous calls to process multiple ODBC calls.</span></span> <span data-ttu-id="bc708-105">あるスレッドが同期 ODBC 呼び出しを実行すると、その呼び出しへの応答を待機するために最初のスレッドがブロックされている間に、他のスレッドの処理を実行できます。</span><span class="sxs-lookup"><span data-stu-id="bc708-105">A thread can make a synchronous ODBC call, and other threads can process while the first thread is blocked waiting for the response to its call.</span></span> <span data-ttu-id="bc708-106">このモデルは、ネットワーク トラフィックなどのオーバーヘッドが取り除かれるので、非同期呼び出しを実行するよりも効率的です。また、ODBC 関数を繰り返し呼び出して SQL_STILL_EXECUTING が返されるかどうかをテストするよりも効率的です。</span><span class="sxs-lookup"><span data-stu-id="bc708-106">This model is more efficient than making asynchronous calls because it eliminates overhead such as network traffic and making repeated ODBC function calls testing for SQL_STILL_EXECUTING.</span></span>  
  
 <span data-ttu-id="bc708-107">それでも、非同期モードは、依然として効果的な処理方法です。</span><span class="sxs-lookup"><span data-stu-id="bc708-107">Asynchronous mode is still an effective method of processing.</span></span> <span data-ttu-id="bc708-108">マルチスレッド モデルによるパフォーマンスの向上は、非同期アプリケーションを書き直すほどのものではありません。</span><span class="sxs-lookup"><span data-stu-id="bc708-108">The performance improvements of a multithreaded model are not enough to justify rewriting asynchronous applications.</span></span> <span data-ttu-id="bc708-109">ユーザーが DB-Library 非同期モデルを使用する DB-Library アプリケーションを ODBC アプリケーションに変換する場合は、ODBC 非同期モデルに変換する方が容易です。</span><span class="sxs-lookup"><span data-stu-id="bc708-109">If users are converting DB-Library applications that use the DB-Library asynchronous model, it is easier to convert them to the ODBC asynchronous model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc708-110">参照</span><span class="sxs-lookup"><span data-stu-id="bc708-110">See Also</span></span>  
 [<span data-ttu-id="bc708-111">SQL Server Native Client ODBC ドライバー アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="bc708-111">Creating a SQL Server Native Client ODBC Driver Application</span></span>](creating-a-driver-application.md)  
  
  
