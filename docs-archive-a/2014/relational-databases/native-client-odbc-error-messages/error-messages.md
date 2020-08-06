---
title: エラーメッセージ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], types
- ODBC error handling, message types
- errors [ODBC], types
ms.assetid: 46c0c22e-d105-4d5b-bb9d-5694472e8651
author: rothja
ms.author: jroth
ms.openlocfilehash: d004ba320b50896b6f57c5de335d7f7b3d33e87a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738322"
---
# <a name="error-messages"></a><span data-ttu-id="e621d-102">エラー メッセージ</span><span class="sxs-lookup"><span data-stu-id="e621d-102">Error Messages</span></span>
  <span data-ttu-id="e621d-103">Native Client ODBC ドライバーによって返されるメッセージのテキスト [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、 **SQLGetDiagRec**の*messagetext*パラメーターに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e621d-103">The text of messages returned by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver is placed in the *MessageText* parameter of **SQLGetDiagRec**.</span></span> <span data-ttu-id="e621d-104">メッセージのヘッダーには、次のようにエラーの発生元が記載されます。</span><span class="sxs-lookup"><span data-stu-id="e621d-104">The source of an error is indicated by the header of the message:</span></span>  
  
 <span data-ttu-id="e621d-105">[Microsoft][ODBC Driver Manager]</span><span class="sxs-lookup"><span data-stu-id="e621d-105">[Microsoft][ODBC Driver Manager]</span></span>  
 <span data-ttu-id="e621d-106">このヘッダーに関連するエラーは、ODBC ドライバー マネージャーで発生しています。</span><span class="sxs-lookup"><span data-stu-id="e621d-106">These errors are raised by the ODBC Driver Manager.</span></span>  
  
 <span data-ttu-id="e621d-107">[Microsoft][ODBC Cursor Library]</span><span class="sxs-lookup"><span data-stu-id="e621d-107">[Microsoft][ODBC Cursor Library]</span></span>  
 <span data-ttu-id="e621d-108">このヘッダーに関連するエラーは、ODBC カーソル ライブラリで発生しています。</span><span class="sxs-lookup"><span data-stu-id="e621d-108">These errors are raised by the ODBC cursor library.</span></span>  
  
 <span data-ttu-id="e621d-109">[Microsoft][SQL Server Native Client]</span><span class="sxs-lookup"><span data-stu-id="e621d-109">[Microsoft][SQL Server Native Client]</span></span>  
 <span data-ttu-id="e621d-110">これらのエラーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーによって発生します。</span><span class="sxs-lookup"><span data-stu-id="e621d-110">These errors are raised by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="e621d-111">Net-Library または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の名前が付いているノードが他にない場合、エラーはドライバー内で発生しています。</span><span class="sxs-lookup"><span data-stu-id="e621d-111">If there are no other nodes with either the name of a Net-Library or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], then the error was encountered in the driver.</span></span>  
  
 <span data-ttu-id="e621d-112">エクスプローラー[SQL Server Native Client][*Net-transportname*]</span><span class="sxs-lookup"><span data-stu-id="e621d-112">[Microsoft][SQL Server Native Client][*Net-Transportname*]</span></span>  
 <span data-ttu-id="e621d-113">これらのエラーは、Net-library によって発生し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 *net-transportname*は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントネットワークトランスポート (名前付きパイプ、共有メモリ、tcp/ip ソケット、VIA など) の表示名です。</span><span class="sxs-lookup"><span data-stu-id="e621d-113">These errors are raised by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Net-Library, where *Net-Transportname* is the display name of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client network transport (for example, Named Pipes, Shared Memory, TCP/IP Sockets, or VIA).</span></span> <span data-ttu-id="e621d-114">エラー メッセージの残りの部分には、呼び出された Net-Library 関数と、TDS 関数から呼び出された基になるネットワーク API の関数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e621d-114">The remainder of the error message contains the Net-Library function called and the function called in the underlying network API by the TDS function.</span></span> <span data-ttu-id="e621d-115">これらのエラーと共に返される*pfNative*エラーコードは、基になるネットワークプロトコルスタックからのエラーコードです。</span><span class="sxs-lookup"><span data-stu-id="e621d-115">The *pfNative* error code returned with these errors is the error code from the underlying network protocol stack.</span></span>  
  
 <span data-ttu-id="e621d-116">[Microsoft][SQL Server Native Client][[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]</span><span class="sxs-lookup"><span data-stu-id="e621d-116">[Microsoft][SQL Server Native Client][[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]</span></span>  
 <span data-ttu-id="e621d-117">このヘッダーに関連するエラーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で発生しています。</span><span class="sxs-lookup"><span data-stu-id="e621d-117">These errors are raised by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e621d-118">エラー メッセージの残りの部分は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー メッセージのテキストです。</span><span class="sxs-lookup"><span data-stu-id="e621d-118">The remainder of the error message is the text of the error message from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e621d-119">これらのエラーと共に返される*pfNative*コードは、からのエラー番号です [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e621d-119">The *pfNative* code returned with these errors is the error number from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e621d-120">によって返されるエラーメッセージの一覧 (およびその番号) の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、の**master**データベースにある**sysmessages**システムテーブルの description 列と error 列を参照してください [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e621d-120">For more information about a list of error messages (and their numbers) that can be returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see the description and error columns of the **sysmessages** system table in the **master** database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e621d-121">参照</span><span class="sxs-lookup"><span data-stu-id="e621d-121">See Also</span></span>  
 [<span data-ttu-id="e621d-122">エラーとメッセージの処理</span><span class="sxs-lookup"><span data-stu-id="e621d-122">Handling Errors and Messages</span></span>](handling-errors-and-messages.md)  
  
  
