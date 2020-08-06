---
title: srv_rpcname (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcname
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcname
ms.assetid: 0a1424e4-3319-4836-b8d8-5e0344cc683f
author: rothja
ms.author: jroth
ms.openlocfilehash: 21530b3e7b8aaa8c5a3f8770762cde7e258e3a43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742117"
---
# <a name="srv_rpcname-extended-stored-procedure-api"></a><span data-ttu-id="632b0-102">srv_rpcname (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="632b0-102">srv_rpcname (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="632b0-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="632b0-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="632b0-104">現在のリモート ストアド プロシージャのプロシージャ名部分を返します。</span><span class="sxs-lookup"><span data-stu-id="632b0-104">Returns the procedure name component for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="632b0-105">構文</span><span class="sxs-lookup"><span data-stu-id="632b0-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_rpcname (  
SRV_PROC *  
srvproc  
,  
int *  
len   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="632b0-106">引数</span><span class="sxs-lookup"><span data-stu-id="632b0-106">Arguments</span></span>  
 <span data-ttu-id="632b0-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="632b0-107">*srvproc*</span></span>  
 <span data-ttu-id="632b0-108">特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="632b0-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="632b0-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="632b0-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="632b0-110">*len*</span><span class="sxs-lookup"><span data-stu-id="632b0-110">*len*</span></span>  
 <span data-ttu-id="632b0-111">データベース名の長さを受け取る整数変数を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="632b0-111">Is a pointer to an integer variable that receives the length of the database name.</span></span> <span data-ttu-id="632b0-112">*len* が NULL である場合、リモート ストアド プロシージャ名の長さは返されていません。</span><span class="sxs-lookup"><span data-stu-id="632b0-112">If *len* is NULL, the length of the remote stored procedure name is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="632b0-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="632b0-113">Returns</span></span>  
 <span data-ttu-id="632b0-114">現在のリモート ストアド プロシージャのリモート ストアド プロシージャ名部分に対応した NULL 終端文字列を指す DBCHAR ポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="632b0-114">A DBCHAR pointer to the null-terminated string for the remote stored procedure name component of the current remote stored procedure.</span></span> <span data-ttu-id="632b0-115">現在のリモート ストアド プロシージャがない場合は、NULL が返され、*len* が -1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="632b0-115">If there is not a current remote stored procedure, NULL is returned and *len* is set to -1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="632b0-116">解説</span><span class="sxs-lookup"><span data-stu-id="632b0-116">Remarks</span></span>  
 <span data-ttu-id="632b0-117">この関数は、リモート ストアド プロシージャの名前のみを返します。</span><span class="sxs-lookup"><span data-stu-id="632b0-117">This function returns only the name of the remote stored procedure.</span></span> <span data-ttu-id="632b0-118">所有者、データベース名、およびリモート ストアド プロシージャ番号に対応する省略可能な指定子は含まれません。</span><span class="sxs-lookup"><span data-stu-id="632b0-118">It does not include the optional specifiers for owner, database name, and remote stored procedure number.</span></span>  
  
 <span data-ttu-id="632b0-119">リモート ストアド プロシージャがなくても **srv_rpcname** を呼び出すことは有効であるため (情報エラーは発生しない)、この関数にはリモート ストアド プロシージャが存在するかどうかを判断する手段が用意されています。</span><span class="sxs-lookup"><span data-stu-id="632b0-119">Because it is valid to call **srv_rpcname** when there is not a remote stored procedure (no informational error occurs), this function provides a method for determining whether a remote stored procedure exists.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="632b0-120">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="632b0-120">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="632b0-121">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="632b0-121">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
