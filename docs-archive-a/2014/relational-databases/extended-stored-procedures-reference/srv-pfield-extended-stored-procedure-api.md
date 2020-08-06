---
title: srv_pfield (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_pfield
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_pfield
ms.assetid: a61e4c1f-e65b-48ea-a7d1-3e1544af389d
author: rothja
ms.author: jroth
ms.openlocfilehash: 90680d59dbf36ad3f713fd7a09d07553890a8668
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742121"
---
# <a name="srv_pfield-extended-stored-procedure-api"></a><span data-ttu-id="ae671-102">srv_pfield (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="ae671-102">srv_pfield (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="ae671-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="ae671-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="ae671-104">データベース接続に関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="ae671-104">Returns information about a database connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae671-105">構文</span><span class="sxs-lookup"><span data-stu-id="ae671-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_pfield (  
SRV_PROC *  
srvproc  
,  
int   
field  
,  
int *  
len  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="ae671-106">引数</span><span class="sxs-lookup"><span data-stu-id="ae671-106">Arguments</span></span>  
 <span data-ttu-id="ae671-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="ae671-107">*srvproc*</span></span>  
 <span data-ttu-id="ae671-108">データベース接続を特定するポインターです。</span><span class="sxs-lookup"><span data-stu-id="ae671-108">Pointer identifying a database connection.</span></span>  
  
 <span data-ttu-id="ae671-109">*分野*</span><span class="sxs-lookup"><span data-stu-id="ae671-109">*field*</span></span>  
 <span data-ttu-id="ae671-110">その接続について返すデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="ae671-110">Specifies data on the connection to return.</span></span>  
  
|<span data-ttu-id="ae671-111">値</span><span class="sxs-lookup"><span data-stu-id="ae671-111">Value</span></span>|<span data-ttu-id="ae671-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="ae671-112">Returns</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="ae671-113">SRV_APPLNAME</span><span class="sxs-lookup"><span data-stu-id="ae671-113">SRV_APPLNAME</span></span>|<span data-ttu-id="ae671-114">接続の確立時にクライアントから提供されたアプリケーション名。</span><span class="sxs-lookup"><span data-stu-id="ae671-114">The application name provided by the client when it established the connection.</span></span>|  
|<span data-ttu-id="ae671-115">SRV_BCPFLAG</span><span class="sxs-lookup"><span data-stu-id="ae671-115">SRV_BCPFLAG</span></span>|<span data-ttu-id="ae671-116">クライアントが一括コピー操作の準備中である場合は TRUE、それ以外の場合は FALSE を示すフラグ。</span><span class="sxs-lookup"><span data-stu-id="ae671-116">A flag that is TRUE if the client is preparing for a bulk copy operation; otherwise, FALSE.</span></span>|  
|<span data-ttu-id="ae671-117">SRV_CLIB</span><span class="sxs-lookup"><span data-stu-id="ae671-117">SRV_CLIB</span></span>|<span data-ttu-id="ae671-118">クライアントがサーバーと通信できるようにするライブラリの名前。</span><span class="sxs-lookup"><span data-stu-id="ae671-118">The name of the library that enables the client to talk to a server.</span></span>|  
|<span data-ttu-id="ae671-119">SRV_CPID</span><span class="sxs-lookup"><span data-stu-id="ae671-119">SRV_CPID</span></span>|<span data-ttu-id="ae671-120">クライアント ソース コンピューターのクライアント プロセス ID。</span><span class="sxs-lookup"><span data-stu-id="ae671-120">The client process ID on the client source computer.</span></span>|  
|<span data-ttu-id="ae671-121">SRV_HOST</span><span class="sxs-lookup"><span data-stu-id="ae671-121">SRV_HOST</span></span>|<span data-ttu-id="ae671-122">接続の確立時にクライアントから提供されたクライアント コンピューターの名前。</span><span class="sxs-lookup"><span data-stu-id="ae671-122">The name of the client's machine provided by the client when it established the connection.</span></span>|  
|<span data-ttu-id="ae671-123">SRV_LIBVERS</span><span class="sxs-lookup"><span data-stu-id="ae671-123">SRV_LIBVERS</span></span>|<span data-ttu-id="ae671-124">クライアント ライブラリのバージョン。</span><span class="sxs-lookup"><span data-stu-id="ae671-124">The version of the client library.</span></span>|  
|<span data-ttu-id="ae671-125">SRV_LSECURE</span><span class="sxs-lookup"><span data-stu-id="ae671-125">SRV_LSECURE</span></span>|<span data-ttu-id="ae671-126">フラグ。</span><span class="sxs-lookup"><span data-stu-id="ae671-126">A flag.</span></span> <span data-ttu-id="ae671-127">その接続で、ログインに統合セキュリティを使用した場合は TRUE を示します。</span><span class="sxs-lookup"><span data-stu-id="ae671-127">TRUE if the connection used integrated security to login.</span></span>|  
|<span data-ttu-id="ae671-128">SRV_NETWORK_MODULE</span><span class="sxs-lookup"><span data-stu-id="ae671-128">SRV_NETWORK_MODULE</span></span>|<span data-ttu-id="ae671-129">接続に使用された Net-Library DLL の名前。</span><span class="sxs-lookup"><span data-stu-id="ae671-129">The name of the Net-Library DLL used by the connection.</span></span>|  
|<span data-ttu-id="ae671-130">SRV_NETWORK_VERSION</span><span class="sxs-lookup"><span data-stu-id="ae671-130">SRV_NETWORK_VERSION</span></span>|<span data-ttu-id="ae671-131">接続に使用された Net-Library DLL のバージョン。</span><span class="sxs-lookup"><span data-stu-id="ae671-131">The version of the Net-Library DLL used by the connection.</span></span>|  
|<span data-ttu-id="ae671-132">SRV_NETWORK_CONNECTION</span><span class="sxs-lookup"><span data-stu-id="ae671-132">SRV_NETWORK_CONNECTION</span></span>|<span data-ttu-id="ae671-133">現在の *srvproc* 接続で使用した Net-Library DLL に渡された接続文字列。</span><span class="sxs-lookup"><span data-stu-id="ae671-133">The connection string passed to the Net-Library DLL used for the current *srvproc* connection.</span></span>|  
|<span data-ttu-id="ae671-134">SRV_PIPEHANDLE</span><span class="sxs-lookup"><span data-stu-id="ae671-134">SRV_PIPEHANDLE</span></span>|<span data-ttu-id="ae671-135">接続されたクライアントのパイプ ハンドルを格納した文字列。名前付きパイプを使用しないネットワークにクライアントが接続されている場合は NULL。</span><span class="sxs-lookup"><span data-stu-id="ae671-135">A string containing the pipe handle of a connected client, or NULL if the client is connected on a network that does not use named pipes.</span></span> <span data-ttu-id="ae671-136">このハンドルを [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows で有効なパイプ ハンドルとして使用するには、この文字列を整数に変換します。</span><span class="sxs-lookup"><span data-stu-id="ae671-136">To use this handle as a valid pipe handle with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, convert this string to an integer.</span></span>|  
|<span data-ttu-id="ae671-137">SRV_RMTSERVER</span><span class="sxs-lookup"><span data-stu-id="ae671-137">SRV_RMTSERVER</span></span>|<span data-ttu-id="ae671-138">クライアント プロセスのログイン元であるサーバー。</span><span class="sxs-lookup"><span data-stu-id="ae671-138">The server from which the client process is logged in.</span></span> <span data-ttu-id="ae671-139">クライアントからのログインの場合、この値は空文字列になります。</span><span class="sxs-lookup"><span data-stu-id="ae671-139">If the login is from a client, this value is an empty string.</span></span>|  
|<span data-ttu-id="ae671-140">SRV_ROWSENT</span><span class="sxs-lookup"><span data-stu-id="ae671-140">SRV_ROWSENT</span></span>|<span data-ttu-id="ae671-141">現在の結果セットについて、*srvproc* で送信済みの行数。</span><span class="sxs-lookup"><span data-stu-id="ae671-141">The number of rows already sent by *srvproc* for the current set of results.</span></span>|  
|<span data-ttu-id="ae671-142">SRV_SPID</span><span class="sxs-lookup"><span data-stu-id="ae671-142">SRV_SPID</span></span>|<span data-ttu-id="ae671-143">*srvproc* のサーバー スレッド ID。</span><span class="sxs-lookup"><span data-stu-id="ae671-143">The server thread ID of the *srvproc*.</span></span> <span data-ttu-id="ae671-144">拡張ストアド プロシージャでは、この値は **sys.sysprocesses** の **kpid** 列に等しく、時間の経過に伴って変化します。</span><span class="sxs-lookup"><span data-stu-id="ae671-144">For extended stored procedures, this value is the same as the **kpid** column of **sys.sysprocesses**, and it can change over time.</span></span>|  
|<span data-ttu-id="ae671-145">SRV_SPROC_CODEPAGE</span><span class="sxs-lookup"><span data-stu-id="ae671-145">SRV_SPROC_CODEPAGE</span></span>|<span data-ttu-id="ae671-146">マルチバイト データを解釈するためにサーバーで使用するコード ページ。</span><span class="sxs-lookup"><span data-stu-id="ae671-146">Codepage that the server uses to interpret multbyte data.</span></span>|  
|<span data-ttu-id="ae671-147">SRV_STATUS</span><span class="sxs-lookup"><span data-stu-id="ae671-147">SRV_STATUS</span></span>|<span data-ttu-id="ae671-148">*srvproc* の現在の状態 (running または closed)。</span><span class="sxs-lookup"><span data-stu-id="ae671-148">The current status of *srvproc*: running or closed</span></span>|  
|<span data-ttu-id="ae671-149">SRV_TYPE</span><span class="sxs-lookup"><span data-stu-id="ae671-149">SRV_TYPE</span></span>|<span data-ttu-id="ae671-150">*srvproc* の接続の種類。</span><span class="sxs-lookup"><span data-stu-id="ae671-150">The connection type of *srvproc*.</span></span> <span data-ttu-id="ae671-151">server が返される場合、*srvproc* は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを拠点としています。</span><span class="sxs-lookup"><span data-stu-id="ae671-151">If server is returned, *srvproc* is from an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ae671-152">client が返される場合、*srvproc* は DB-Library クライアントまたは ODBC クライアントを拠点としています。</span><span class="sxs-lookup"><span data-stu-id="ae671-152">If client is returned, *srvproc* is from a DB-Library or ODBC client.</span></span>|  
|<span data-ttu-id="ae671-153">SRV_USER</span><span class="sxs-lookup"><span data-stu-id="ae671-153">SRV_USER</span></span>|<span data-ttu-id="ae671-154">接続のユーザー名。</span><span class="sxs-lookup"><span data-stu-id="ae671-154">The user name of the connection.</span></span>|  
|||  
  
 <span data-ttu-id="ae671-155">*len*</span><span class="sxs-lookup"><span data-stu-id="ae671-155">*len*</span></span>  
 <span data-ttu-id="ae671-156">返された *field* 値の長さを格納した **int** 型変数を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="ae671-156">Is a pointer to an **int** variable that contains the length of the returned *field* value.</span></span> <span data-ttu-id="ae671-157">*len* が NULL の場合、文字列の長さは返されていません。</span><span class="sxs-lookup"><span data-stu-id="ae671-157">If *len* is NULL, the length of the string is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="ae671-158">戻り値</span><span class="sxs-lookup"><span data-stu-id="ae671-158">Returns</span></span>  
 <span data-ttu-id="ae671-159">SRV_PROC 構造体にある指定されたフィールドの現在値を格納した NULL 終端文字列へのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="ae671-159">A pointer to a null-terminated string containing the current value for the specified field in the SRV_PROC structure.</span></span> <span data-ttu-id="ae671-160">フィールドが空の場合は空文字列への有効なポインターが返され、*len* は 0 になります。</span><span class="sxs-lookup"><span data-stu-id="ae671-160">If the field is empty, a valid pointer to an empty string is returned and *len* contains 0.</span></span> <span data-ttu-id="ae671-161">フィールドが指定されていない場合は NULL を返し、*len* は -1 になります。</span><span class="sxs-lookup"><span data-stu-id="ae671-161">If the field is unknown, NULL is returned and *len* contains the value -1.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ae671-162">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae671-162">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="ae671-163">セキュリティの確認とテストについては、「[セキュリティ TechCenter](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ae671-163">For information about security review and testing, see the [Security Developer Center](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
