---
title: MSSQLSERVER_33081 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33081 (Database Engine error)
ms.assetid: 839705e7-fa37-4c0d-9f3f-95a9eab98bcf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0752220cc20641d9b51a3a66fecc86f9efd63433
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640022"
---
# <a name="mssqlserver_33081"></a><span data-ttu-id="06508-102">MSSQLSERVER_33081</span><span class="sxs-lookup"><span data-stu-id="06508-102">MSSQLSERVER_33081</span></span>
    
## <a name="details"></a><span data-ttu-id="06508-103">詳細</span><span class="sxs-lookup"><span data-stu-id="06508-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="06508-104">製品名</span><span class="sxs-lookup"><span data-stu-id="06508-104">Product Name</span></span>|<span data-ttu-id="06508-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="06508-105">SQL Server</span></span>|  
|<span data-ttu-id="06508-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="06508-106">Event ID</span></span>|<span data-ttu-id="06508-107">33081</span><span class="sxs-lookup"><span data-stu-id="06508-107">33081</span></span>|  
|<span data-ttu-id="06508-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="06508-108">Event Source</span></span>|<span data-ttu-id="06508-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="06508-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="06508-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="06508-110">Component</span></span>|<span data-ttu-id="06508-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="06508-111">SQLEngine</span></span>|  
|<span data-ttu-id="06508-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="06508-112">Symbolic Name</span></span>|<span data-ttu-id="06508-113">SEC_DLL_TRUST_VERIFICATION_FAILED</span><span class="sxs-lookup"><span data-stu-id="06508-113">SEC_DLL_TRUST_VERIFICATION_FAILED</span></span>|  
|<span data-ttu-id="06508-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="06508-114">Message Text</span></span>|<span data-ttu-id="06508-115">Authenticode 署名またはファイル パスが無効なため、暗号プロバイダー '%.\*ls' を読み込めませんでした。</span><span class="sxs-lookup"><span data-stu-id="06508-115">Failed to load cryptographic provider '%.\*ls' due to an invalid Authenticode signature or invalid file path.</span></span>  <span data-ttu-id="06508-116">前のメッセージでその他のエラーを確認してください。</span><span class="sxs-lookup"><span data-stu-id="06508-116">Check previous messages for other failures.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="06508-117">説明</span><span class="sxs-lookup"><span data-stu-id="06508-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="06508-118">は、エラー メッセージに表示されている暗号化サービス プロバイダーを読み込めませんでした。</span><span class="sxs-lookup"><span data-stu-id="06508-118">was unable to load the cryptographic provider listed in the error message.</span></span> <span data-ttu-id="06508-119">このエラーの原因と考えられる Win API エラーがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="06508-119">There are several Win API failures which might cause this error.</span></span> <span data-ttu-id="06508-120">リング バッファーに、失敗した API の名前とその API によって返された Windows エラー コードが格納されています。</span><span class="sxs-lookup"><span data-stu-id="06508-120">The ring buffer contains the name of the failed API and the Windows error code returned by the API.</span></span> <span data-ttu-id="06508-121">詳細情報を表示するには、次のクエリを使用して sys.dm_os_ring_buffers ビューにクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="06508-121">To get more information, query the sys.dm_os_ring_buffers view using the following query.</span></span>  
  
```  
SELECT * FROM sys.dm_os_ring_buffers   
WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
```  
  
## <a name="user-action"></a><span data-ttu-id="06508-122">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="06508-122">User Action</span></span>  
 <span data-ttu-id="06508-123">問題を調査するには、MSDN (https://msdn.microsoft.com/) で Windows エラー コードを検索します。</span><span class="sxs-lookup"><span data-stu-id="06508-123">To investigate the problem, search for the Windows error code in MSDN (https://msdn.microsoft.com/).</span></span> <span data-ttu-id="06508-124">エラーを解決するか、詳細について [!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS に問い合わせます。</span><span class="sxs-lookup"><span data-stu-id="06508-124">Resolve the error, or contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS for more information.</span></span> <span data-ttu-id="06508-125">CSS へのお問い合わせの際には、次の情報を収集してサポート スタッフにご提供ください。</span><span class="sxs-lookup"><span data-stu-id="06508-125">If you need to contact CSS, collect the following information for our support staff.</span></span>  
  
-   <span data-ttu-id="06508-126">暗号化サービス プロバイダーの読み込み失敗に関するエラーを示すエラー ログ。</span><span class="sxs-lookup"><span data-stu-id="06508-126">The error log showing the failed to load cryptographic provider error.</span></span>  
  
-   <span data-ttu-id="06508-127">次のステートメントからの出力。</span><span class="sxs-lookup"><span data-stu-id="06508-127">The output from the following statement:</span></span>  
  
    ```  
    SELECT * FROM sys.dm_os_ring_buffers   
    WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
    ```  
  
> [!NOTE]  
>  <span data-ttu-id="06508-128">リング バッファー情報は再起動時に失われる場合があるため、すばやく収集してください。</span><span class="sxs-lookup"><span data-stu-id="06508-128">Try to collect the ring buffer information promptly as ring buffer information can be lost during a restart.</span></span>  
  
  
