---
title: MSSQLSERVER_26014 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 26014 (Database Engine error)
ms.assetid: e2b0dfc7-0681-4e5d-8875-1d5f63534086
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8114183b212767d01013eee9387d8b2efa2e0d7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641000"
---
# <a name="mssqlserver_26014"></a><span data-ttu-id="69439-102">MSSQLSERVER_26014</span><span class="sxs-lookup"><span data-stu-id="69439-102">MSSQLSERVER_26014</span></span>
    
## <a name="details"></a><span data-ttu-id="69439-103">詳細</span><span class="sxs-lookup"><span data-stu-id="69439-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="69439-104">製品名</span><span class="sxs-lookup"><span data-stu-id="69439-104">Product Name</span></span>|<span data-ttu-id="69439-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="69439-105">SQL Server</span></span>|  
|<span data-ttu-id="69439-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="69439-106">Event ID</span></span>|<span data-ttu-id="69439-107">26014</span><span class="sxs-lookup"><span data-stu-id="69439-107">26014</span></span>|  
|<span data-ttu-id="69439-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="69439-108">Event Source</span></span>|<span data-ttu-id="69439-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="69439-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="69439-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="69439-110">Component</span></span>|<span data-ttu-id="69439-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="69439-111">SQLEngine</span></span>|  
|<span data-ttu-id="69439-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="69439-112">Symbolic Name</span></span>|<span data-ttu-id="69439-113">SNI_SSL_USER_CERT_FAILURE</span><span class="sxs-lookup"><span data-stu-id="69439-113">SNI_SSL_USER_CERT_FAILURE</span></span>|  
|<span data-ttu-id="69439-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="69439-114">Message Text</span></span>|<span data-ttu-id="69439-115">ユーザーが指定した証明書 [Cert Hash(sha1) "%hs"] を読み込むことができません。</span><span class="sxs-lookup"><span data-stu-id="69439-115">Unable to load user-specified certificate [Cert Hash(sha1) "%hs"].</span></span> <span data-ttu-id="69439-116">サーバー側では接続が許可されません。</span><span class="sxs-lookup"><span data-stu-id="69439-116">The server will not accept a connection.</span></span> <span data-ttu-id="69439-117">証明書が正しくインストールされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="69439-117">You should verify that the certificate is correctly installed.</span></span> <span data-ttu-id="69439-118">オンライン ブックの「SSL に使用する証明書の構成」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69439-118">See "Configuring Certificate for Use by SSL" in Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="69439-119">説明</span><span class="sxs-lookup"><span data-stu-id="69439-119">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="69439-120">は、メッセージで指定された証明書を読み込もうとしましたが、読み込み操作に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="69439-120">attempted to load the certificate named in the message but the operation failed.</span></span> <span data-ttu-id="69439-121">この証明書を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用するには、この問題を解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="69439-121">This problem must be resolved before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can use this certificate.</span></span>  
  
 <span data-ttu-id="69439-122">エラーの原因として以下が考えられます。</span><span class="sxs-lookup"><span data-stu-id="69439-122">Possible causes of the error include:</span></span>  
  
-   <span data-ttu-id="69439-123">証明書が移動または削除されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="69439-123">The certificate could have been moved or deleted.</span></span>  
  
-   <span data-ttu-id="69439-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が使用するログインを変更した場合は、証明書にアクセスする権限が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="69439-124">If the login used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has changed, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may not have permission to access the certificate.</span></span>  
  
-   <span data-ttu-id="69439-125">証明書の有効期限が切れている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="69439-125">The certificate may have expired.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="69439-126">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="69439-126">User Action</span></span>  
 <span data-ttu-id="69439-127">メッセージで指定された証明書がシステム上に存在すること、その証明書にアクセスできること、およびその証明書が使用可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="69439-127">Make sure the certificate named in the message exists on the system, is accessible, and it is valid for use.</span></span>  
  
  
