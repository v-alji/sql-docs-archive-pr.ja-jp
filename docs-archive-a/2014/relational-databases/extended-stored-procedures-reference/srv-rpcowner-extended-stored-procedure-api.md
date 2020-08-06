---
title: srv_rpcowner (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcowner
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcowner
ms.assetid: e81a60e6-14ea-47bc-a11c-3d7635344447
author: rothja
ms.author: jroth
ms.openlocfilehash: f903870d0ee01256addb1557eb7e9123853b39e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743246"
---
# <a name="srv_rpcowner-extended-stored-procedure-api"></a><span data-ttu-id="b9cd6-102">srv_rpcowner (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="b9cd6-102">srv_rpcowner (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="b9cd6-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="b9cd6-104">現在のリモート ストアド プロシージャの所有者部分を返します。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-104">Returns the owner component for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9cd6-105">構文</span><span class="sxs-lookup"><span data-stu-id="b9cd6-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_rpcowner (  
SRV_PROC *  
srvproc  
,  
int *  
len   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="b9cd6-106">引数</span><span class="sxs-lookup"><span data-stu-id="b9cd6-106">Arguments</span></span>  
 <span data-ttu-id="b9cd6-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="b9cd6-107">*srvproc*</span></span>  
 <span data-ttu-id="b9cd6-108">特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="b9cd6-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="b9cd6-110">*len*</span><span class="sxs-lookup"><span data-stu-id="b9cd6-110">*len*</span></span>  
 <span data-ttu-id="b9cd6-111">所有者名の長さを受け取る整数変数を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-111">Is a pointer to an integer variable that receives the length of the owner name.</span></span> <span data-ttu-id="b9cd6-112">パラメーター *len* は NULL になる場合があります。NULL 値の場合、所有者部分の長さは返されていません。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-112">The parameter *len* can be NULL, in which case the length of the owner component is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="b9cd6-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="b9cd6-113">Returns</span></span>  
 <span data-ttu-id="b9cd6-114">現在のリモート ストアド プロシージャの所有者部分を表した  NULL 終端文字列を指す DBCHAR ポインターです。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-114">A DBCHAR pointer to the null-terminated owner component for the current remote stored procedure.</span></span> <span data-ttu-id="b9cd6-115">現在のリモート ストアド プロシージャがない場合は、NULL が返され、*len* が - 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-115">If there is no current remote stored procedure, NULL is returned and *len* is set to - 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9cd6-116">解説</span><span class="sxs-lookup"><span data-stu-id="b9cd6-116">Remarks</span></span>  
 <span data-ttu-id="b9cd6-117">この関数は、リモート ストアド プロシージャの所有者部分だけを返します。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-117">This function returns only the owner component of the remote stored procedure.</span></span> <span data-ttu-id="b9cd6-118">名前、リモート ストアド プロシージャ名、およびリモート ストアド プロシージャ番号の省略可能な各指定子は含まれません。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-118">It does not include the optional specifiers for name, remote stored procedure name, and remote stored procedure number.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b9cd6-119">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-119">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="b9cd6-120">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b9cd6-120">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
