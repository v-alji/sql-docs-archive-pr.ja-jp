---
title: srv_rpcnumber (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcnumber
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcnumber
ms.assetid: 3094085e-fe9e-423d-bf87-7852352c2d26
author: rothja
ms.author: jroth
ms.openlocfilehash: 25f30f8288125cf64d6b10a867d6af03c0f8ee91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742114"
---
# <a name="srv_rpcnumber-extended-stored-procedure-api"></a><span data-ttu-id="09933-102">srv_rpcnumber (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="09933-102">srv_rpcnumber (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="09933-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="09933-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="09933-104">現在のリモート ストアド プロシージャ呼び出しの番号部分を返します。</span><span class="sxs-lookup"><span data-stu-id="09933-104">Returns the number component for the current remote stored procedure call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09933-105">構文</span><span class="sxs-lookup"><span data-stu-id="09933-105">Syntax</span></span>  
  
```  
  
int srv_rpcnumber ( SRV_PROC *  
srvproc   
)  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="09933-106">引数</span><span class="sxs-lookup"><span data-stu-id="09933-106">Arguments</span></span>  
 <span data-ttu-id="09933-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="09933-107">*srvproc*</span></span>  
 <span data-ttu-id="09933-108">特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="09933-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="09933-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="09933-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="09933-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="09933-110">Returns</span></span>  
 <span data-ttu-id="09933-111">現在のリモート ストアド プロシージャの番号部分です。</span><span class="sxs-lookup"><span data-stu-id="09933-111">The number component for the current remote stored procedure.</span></span> <span data-ttu-id="09933-112">クライアントがリモート ストアド プロシージャの実行時に番号部分を使用していない場合、またはリモート ストアド プロシージャがない場合は、-1 を返します。</span><span class="sxs-lookup"><span data-stu-id="09933-112">If the client does not use a number component when running the remote stored procedure or if there is no current remote stored procedure, it returns - 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09933-113">解説</span><span class="sxs-lookup"><span data-stu-id="09933-113">Remarks</span></span>  
 <span data-ttu-id="09933-114">この関数は、リモート ストアド プロシージャの番号部分のみを返します。</span><span class="sxs-lookup"><span data-stu-id="09933-114">This function returns only the number component of the remote stored procedure.</span></span> <span data-ttu-id="09933-115">所有者、リモート ストアド プロシージャ名、およびデータベース名の省略可能な指定子は含まれません。</span><span class="sxs-lookup"><span data-stu-id="09933-115">It does not include the optional specifiers for owner, remote stored procedure name, and database name.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="09933-116">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="09933-116">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="09933-117">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="09933-117">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
