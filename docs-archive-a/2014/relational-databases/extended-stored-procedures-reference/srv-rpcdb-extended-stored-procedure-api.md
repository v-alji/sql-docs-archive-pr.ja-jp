---
title: srv_rpcdb (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcdb
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcdb
ms.assetid: d52bfd22-7a7c-4ab0-af65-df96ff359e6f
author: rothja
ms.author: jroth
ms.openlocfilehash: c951a4a821bbd49748182d9ddf5df017344a174d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739990"
---
# <a name="srv_rpcdb-extended-stored-procedure-api"></a><span data-ttu-id="73e78-102">srv_rpcdb (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="73e78-102">srv_rpcdb (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="73e78-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="73e78-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="73e78-104">現在のリモート ストアド プロシージャのデータベース名部分を返します。</span><span class="sxs-lookup"><span data-stu-id="73e78-104">Returns the database name component for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73e78-105">構文</span><span class="sxs-lookup"><span data-stu-id="73e78-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_rpcdb (  
SRV_PROC * srvproc,int *len );  
```  
  
## <a name="arguments"></a><span data-ttu-id="73e78-106">引数</span><span class="sxs-lookup"><span data-stu-id="73e78-106">Arguments</span></span>  
 <span data-ttu-id="73e78-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="73e78-107">*srvproc*</span></span>  
 <span data-ttu-id="73e78-108">特定のクライアント接続のためのハンドルである SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="73e78-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="73e78-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="73e78-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="73e78-110">*len*</span><span class="sxs-lookup"><span data-stu-id="73e78-110">*len*</span></span>  
 <span data-ttu-id="73e78-111">データベース名の長さを受け取る `int` 型変数を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="73e78-111">Is a pointer to an `int` variable that receives the length of the database name.</span></span> <span data-ttu-id="73e78-112">*len* が NULL の場合、データベース名の長さは返されていません。</span><span class="sxs-lookup"><span data-stu-id="73e78-112">If *len* is NULL, the length of the database name is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="73e78-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="73e78-113">Returns</span></span>  
 <span data-ttu-id="73e78-114">現在のリモート ストアド プロシージャの名前部分を表した NULL 終端文字列を指す DBCHAR ポインターです。</span><span class="sxs-lookup"><span data-stu-id="73e78-114">A DBCHAR pointer to the null-terminated string for the database name part of the current remote stored procedure.</span></span> <span data-ttu-id="73e78-115">現在のリモート ストアド プロシージャがない場合は、NULL が返され、*len* パラメーターが - 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="73e78-115">If there is no current remote stored procedure, NULL is returned and the *len* parameter is set to - 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73e78-116">解説</span><span class="sxs-lookup"><span data-stu-id="73e78-116">Remarks</span></span>  
 <span data-ttu-id="73e78-117">この関数は、リモート ストアド プロシージャ オブジェクト名のデータベース部分だけを返します。</span><span class="sxs-lookup"><span data-stu-id="73e78-117">This function returns only the database component of the remote stored procedure object name.</span></span> <span data-ttu-id="73e78-118">所有者、リモート ストアド プロシージャ名、およびリモート ストアド プロシージャ番号に対応する省略可能な各指定子は含まれません。</span><span class="sxs-lookup"><span data-stu-id="73e78-118">It does not include the optional specifiers for owner, remote stored procedure name, and remote stored procedure number.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="73e78-119">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="73e78-119">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="73e78-120">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="73e78-120">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
