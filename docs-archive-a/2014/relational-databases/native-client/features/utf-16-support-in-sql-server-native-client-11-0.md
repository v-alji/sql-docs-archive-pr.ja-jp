---
title: SQL Server Native Client 11.0 | での UTF-16 のサポートMicrosoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
author: rothja
ms.author: jroth
ms.openlocfilehash: af8581071400db888fb508b88f8e8ae93bc71f70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643275"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a><span data-ttu-id="c714c-102">SQL Server Native Client 11.0 での UTF-16 のサポート</span><span class="sxs-lookup"><span data-stu-id="c714c-102">UTF-16 Support in SQL Server Native Client 11.0</span></span>
  <span data-ttu-id="c714c-103">以降では [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 、列の結果または出力パラメーターをバインドするときに固定長バッファーを指定し、 `wchar` 終端文字の前にバッファーに書き込まれる文字がサロゲートペアの上位サロゲートコードポイントである場合、および次の文字が下位サロゲートコードポイントである場合、 `wchar` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はバッファーに上位サロゲートコードポイントを追加しません。</span><span class="sxs-lookup"><span data-stu-id="c714c-103">Beginning in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], if you supply a fixed-length buffer when binding a column result or output parameter and if the `wchar` character written into the buffer before the terminating character is a high surrogate code point of a surrogate pair, and if the next `wchar` character is a low surrogate code point, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client will not add the high surrogate code point to the buffer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c714c-104">参照</span><span class="sxs-lookup"><span data-stu-id="c714c-104">See Also</span></span>  
 [<span data-ttu-id="c714c-105">SQL Server Native Client の機能</span><span class="sxs-lookup"><span data-stu-id="c714c-105">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
