---
title: srv_message_handler (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_message_handler
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_message_handler
ms.assetid: 41bcd057-436f-4fa8-8293-fc8057a30877
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e7b6472ed4fabb6dc2d545eb51a1e026635ce19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633853"
---
# <a name="srv_message_handler-extended-stored-procedure-api"></a><span data-ttu-id="117a9-102">srv_message_handler (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="117a9-102">srv_message_handler (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="117a9-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="117a9-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="117a9-104">インストールされている拡張ストアド プロシージャ API メッセージ ハンドラーを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="117a9-104">Calls the installed Extended Stored Procedure API message handler.</span></span> <span data-ttu-id="117a9-105">この関数は、通常、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 拡張ストアドプロシージャからを呼び出して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーログファイルまたは Windows アプリケーションログにエラー (拡張ストアドプロシージャで定義) を記録するために使用され [!INCLUDE[msCoName](../../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="117a9-105">This function is usually used to call [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from an extended stored procedure to log an error (defined by the extended stored procedure) in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log file or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application log.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="117a9-106">構文</span><span class="sxs-lookup"><span data-stu-id="117a9-106">Syntax</span></span>  
  
```  
  
int srv_message_handler (  
SRV_PROC *  
srvproc  
,  
int  
errornum  
,  
BYTE   
severity  
,  
BYTE  
state  
,  
int  
oserrnum  
,  
char *  
errtext  
,  
int  
errtextlen  
,  
char *  
oserrtext  
,  
int  
oserrtextlen  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="117a9-107">引数</span><span class="sxs-lookup"><span data-stu-id="117a9-107">Arguments</span></span>  
 <span data-ttu-id="117a9-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="117a9-108">*srvproc*</span></span>  
 <span data-ttu-id="117a9-109">特定のクライアント接続のためのハンドルである SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="117a9-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="117a9-110">*srvproc* パラメーターには、アプリケーションとクライアント間の通信やデータを管理するために使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="117a9-110">The *srvproc* parameter contains information that is used to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="117a9-111">*errornum*</span><span class="sxs-lookup"><span data-stu-id="117a9-111">*errornum*</span></span>  
 <span data-ttu-id="117a9-112">拡張ストアド プロシージャが定義するエラー番号です。</span><span class="sxs-lookup"><span data-stu-id="117a9-112">Is an error number defined by the extended stored procedure.</span></span> <span data-ttu-id="117a9-113">この値の有効値は 50,001 から 2,147,483,647 です。</span><span class="sxs-lookup"><span data-stu-id="117a9-113">This number must be from 50,001 through 2,147,483,647.</span></span>  
  
 <span data-ttu-id="117a9-114">*severity*</span><span class="sxs-lookup"><span data-stu-id="117a9-114">*severity*</span></span>  
 <span data-ttu-id="117a9-115">エラーに関する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の重大度を示す標準の値です。</span><span class="sxs-lookup"><span data-stu-id="117a9-115">Is a standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] severity value for the error.</span></span> <span data-ttu-id="117a9-116">この値の有効値は 0 ～ 24 です。</span><span class="sxs-lookup"><span data-stu-id="117a9-116">This number must be from 0 through 24.</span></span>  
  
 <span data-ttu-id="117a9-117">*状態*</span><span class="sxs-lookup"><span data-stu-id="117a9-117">*state*</span></span>  
 <span data-ttu-id="117a9-118">エラーに関する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の状態値です。</span><span class="sxs-lookup"><span data-stu-id="117a9-118">Is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] state value for the error.</span></span>  
  
 <span data-ttu-id="117a9-119">*oserrnum*</span><span class="sxs-lookup"><span data-stu-id="117a9-119">*oserrnum*</span></span>  
 <span data-ttu-id="117a9-120">オペレーティング システムのエラー番号です。</span><span class="sxs-lookup"><span data-stu-id="117a9-120">Is the operating-system error number.</span></span> <span data-ttu-id="117a9-121">この引数は無視されます。</span><span class="sxs-lookup"><span data-stu-id="117a9-121">This argument is ignored.</span></span>  
  
 <span data-ttu-id="117a9-122">*errtext*</span><span class="sxs-lookup"><span data-stu-id="117a9-122">*errtext*</span></span>  
 <span data-ttu-id="117a9-123">拡張ストアド プロシージャのエラー *errornum* の説明です。</span><span class="sxs-lookup"><span data-stu-id="117a9-123">Is the description of the extended stored procedure error *errornum*.</span></span>  
  
 <span data-ttu-id="117a9-124">*errtextlen*</span><span class="sxs-lookup"><span data-stu-id="117a9-124">*errtextlen*</span></span>  
 <span data-ttu-id="117a9-125">拡張ストアド プロシージャのエラー文字列 *errtext* の長さです。</span><span class="sxs-lookup"><span data-stu-id="117a9-125">Is the length of the extended stored procedure error string *errtext*.</span></span>  
  
 <span data-ttu-id="117a9-126">*oserrtext*</span><span class="sxs-lookup"><span data-stu-id="117a9-126">*oserrtext*</span></span>  
 <span data-ttu-id="117a9-127">オペレーティング システムのエラー *oserrnum* の説明です。</span><span class="sxs-lookup"><span data-stu-id="117a9-127">Is the description of the operating-system error *oserrnum*.</span></span> <span data-ttu-id="117a9-128">この引数は無視されます。</span><span class="sxs-lookup"><span data-stu-id="117a9-128">This argument is ignored.</span></span>  
  
 <span data-ttu-id="117a9-129">*oserrtextlen*</span><span class="sxs-lookup"><span data-stu-id="117a9-129">*oserrtextlen*</span></span>  
 <span data-ttu-id="117a9-130">オペレーティング システムのエラー文字列 *oserrtext* の長さです。</span><span class="sxs-lookup"><span data-stu-id="117a9-130">Is the length of the operating-system error string *oserrtext*.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="117a9-131">戻り値</span><span class="sxs-lookup"><span data-stu-id="117a9-131">Returns</span></span>  
 <span data-ttu-id="117a9-132">SUCCEED または FAIL。</span><span class="sxs-lookup"><span data-stu-id="117a9-132">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="117a9-133">解説</span><span class="sxs-lookup"><span data-stu-id="117a9-133">Remarks</span></span>  
 <span data-ttu-id="117a9-134">**srv_message_handler** 関数を使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の集中型エラー ログ機能とレポート機能に拡張ストアド プロシージャを統合できるようになります。</span><span class="sxs-lookup"><span data-stu-id="117a9-134">The **srv_message_handler** function enables an extended stored procedure to integrate with the centralized error logging and reporting features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="117a9-135">拡張ストアド プロシージャからのイベントに対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の警告を設定し、警告条件を SQL Server エージェントで監視できます。</span><span class="sxs-lookup"><span data-stu-id="117a9-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alerts can be established for events from extended stored procedures, and SQL Server Agent will monitor for these alert conditions.</span></span>  
  
 <span data-ttu-id="117a9-136">エラー メッセージが長い場合は、412 バイトに切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="117a9-136">If the error message is longer, it is truncated to 412 bytes.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="117a9-137">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="117a9-137">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="117a9-138">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="117a9-138">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
