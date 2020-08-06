---
title: 拡張ストアドプロシージャのしくみ |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], about extended stored procedures
ms.assetid: 6e946d8c-3268-4b59-8a1c-1637909cd701
author: rothja
ms.author: jroth
ms.openlocfilehash: 75082fed6b70c214b4f55b85034ffa371824d24f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643356"
---
# <a name="how-extended-stored-procedures-work"></a><span data-ttu-id="ad2fb-102">拡張ストアド プロシージャのしくみ</span><span class="sxs-lookup"><span data-stu-id="ad2fb-102">How Extended Stored Procedures Work</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="ad2fb-103">代わりに CLR Integration を使用してください。</span><span class="sxs-lookup"><span data-stu-id="ad2fb-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="ad2fb-104">拡張ストアド プロシージャが動作するプロセスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ad2fb-104">The process by which an extended stored procedure works is:</span></span>  
  
1.  <span data-ttu-id="ad2fb-105">クライアントが拡張ストアドプロシージャを実行すると、要求はクライアントアプリケーションからに表形式のデータストリーム (TDS) 形式または Simple Object Access Protocol (SOAP) 形式で送信され [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ad2fb-105">When a client executes an extended stored procedure, the request is transmitted in tabular data stream (TDS) or Simple Object Access Protocol (SOAP) format from the client application to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ad2fb-106">は拡張ストアド プロシージャに関連付けられた DLL を検索し、対象の DLL がまだロードされていない場合はロードします。</span><span class="sxs-lookup"><span data-stu-id="ad2fb-106">searches for the DLL associated with the extended stored procedure, and loads the DLL if it is not already loaded.</span></span>  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ad2fb-107">は、要求されている拡張ストアド プロシージャ (DLL 内に関数として実装されている) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ad2fb-107">calls the requested extended stored procedure (implemented as a function inside the DLL).</span></span>  
  
4.  <span data-ttu-id="ad2fb-108">拡張ストアド プロシージャは拡張ストアド プロシージャ API を介してサーバーに結果セットを渡し、パラメーターを返します。</span><span class="sxs-lookup"><span data-stu-id="ad2fb-108">The extended stored procedure passes result sets and return parameters back to the server by through the Extended Stored Procedure API.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad2fb-109">参照</span><span class="sxs-lookup"><span data-stu-id="ad2fb-109">See Also</span></span>  
 [<span data-ttu-id="ad2fb-110">データベース エンジン拡張ストアド プロシージャ プログラミング</span><span class="sxs-lookup"><span data-stu-id="ad2fb-110">Database Engine Extended Stored Procedure Programming</span></span>](../database-engine-extended-stored-procedure-programming.md)  
  
  
