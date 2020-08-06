---
title: srv_got_attention (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_got_attention
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_got_attention
ms.assetid: 805e68e1-d17f-41bd-8b9f-a27283bb6fbe
author: rothja
ms.author: jroth
ms.openlocfilehash: bb5432e2f5e259187e506237842fbb9110e27a69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742141"
---
# <a name="srv_got_attention-extended-stored-procedure-api"></a><span data-ttu-id="60ac6-102">srv_got_attention (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="60ac6-102">srv_got_attention (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="60ac6-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="60ac6-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="60ac6-104">現在の接続またはタスクを中断する必要があるかどうかをチェックし、接続が強制終了された場合、またはバッチが中断された場合に TRUE を返します。</span><span class="sxs-lookup"><span data-stu-id="60ac6-104">Checks whether the current connection or task needs to be aborted and returns TRUE if the connection is killed or the batch is aborted</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60ac6-105">構文</span><span class="sxs-lookup"><span data-stu-id="60ac6-105">Syntax</span></span>  
  
```  
  
BOOL srv_got_attention  
(SRV_PROC *  
srvproc  
);  
  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60ac6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60ac6-106">Parameters</span></span>  
 <span data-ttu-id="60ac6-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="60ac6-107">*srvproc*</span></span>  
 <span data-ttu-id="60ac6-108">データベース接続を特定するポインターです。</span><span class="sxs-lookup"><span data-stu-id="60ac6-108">Pointer identifying a database connection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60ac6-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="60ac6-109">Return Value</span></span>  
 <span data-ttu-id="60ac6-110">接続が強制終了されたか、バッチが中断された場合に TRUE を返します。</span><span class="sxs-lookup"><span data-stu-id="60ac6-110">TRUE if the connection is killed or the batch is aborted.</span></span> <span data-ttu-id="60ac6-111">接続またはバッチがアクティブであれば FALSE を返します。</span><span class="sxs-lookup"><span data-stu-id="60ac6-111">FALSE if the connection or batch is active.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60ac6-112">解説</span><span class="sxs-lookup"><span data-stu-id="60ac6-112">Remarks</span></span>  
 <span data-ttu-id="60ac6-113">実行時間の長い拡張ストアド プロシージャの場合は、**srv_got_attention** を定期的に呼び出してサーバーのアテンションをチェックすることにより、接続が強制終了されたかバッチが中断されたときに、そのプロシージャが自身を終了できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="60ac6-113">A long-running extended stored procedure should check the server attention by calling **srv_got_attention** periodically so that the procedure may terminate itself when the connection is killed or the batch is aborted.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="60ac6-114">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="60ac6-114">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="60ac6-115">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="60ac6-115">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
