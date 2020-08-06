---
title: バージョン間の互換性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
author: rothja
ms.author: jroth
ms.openlocfilehash: af434713946f5c568ee71644a7403f9496a8c16f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643820"
---
# <a name="cross-version-compatibility"></a><span data-ttu-id="7b92d-102">複数バージョン間の互換性</span><span class="sxs-lookup"><span data-stu-id="7b92d-102">Cross-Version Compatibility</span></span>
  <span data-ttu-id="7b92d-103">バージョン間の競合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] のクライアント インスタンスまたはサーバー インスタンスでテーブル値パラメーターを処理する必要がある場合に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="7b92d-103">Cross-version conflicts can occur when client or server instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] are expected to process table-valued parameters.</span></span>  
  
 <span data-ttu-id="7b92d-104">一般に、テーブル値パラメーターの機能を使用できるのは、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (以降) のサーバーに接続されている [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のクライアント (SQL Server Native Client 10.0 を使用) だけです。</span><span class="sxs-lookup"><span data-stu-id="7b92d-104">In general, table-valued parameter functionality is only available to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] clients (using SQL Server Native Client 10.0) or later that are connected to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (or later) servers.</span></span> <span data-ttu-id="7b92d-105">カタログ関数の結果セットの新しい列は、以降のサーバーに接続されている場合にのみ存在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="7b92d-105">New columns in catalog function result sets will only be present when connected to a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (or later) server.</span></span>  
  
 <span data-ttu-id="7b92d-106">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client でコンパイルされたクライアント アプリケーションで、テーブル値パラメーターが必要なステートメントを実行すると、サーバーではデータ変換エラーからこの状態が検出され、ODBC によって、これが "データ型の属性に関する制限に違反しました" というメッセージの SQLSTATE 07006 として返されます。</span><span class="sxs-lookup"><span data-stu-id="7b92d-106">If a client application compiled with an earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client executes statements that expect table-valued parameters, the server detects this condition through a data conversion error, and ODBC returns this as a SQLSTATE 07006 and the message "Restricted data type attribute violation".</span></span>  
  
 <span data-ttu-id="7b92d-107">Native Client 10.0 以降でコンパイルされたクライアントアプリケーションが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のサーバーインスタンスに接続したときにテーブル値パラメーターを使用しようとした場合、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native client はこれを検出し、SQLBindCol、SQLBindParameter、SQLSetDescFields、SQLSetDescRec の呼び出しは SQLSTATE 07006 で失敗し、メッセージ "制限付き SQL Server のデータ型属性違反 (この接続のバージョンはテーブル値パラメーターを</span><span class="sxs-lookup"><span data-stu-id="7b92d-107">If a client application that was compiled with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 or later tries to use table-valued parameters when connected to a server instance earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client will detect this, and SQLBindCol, SQLBindParameter, SQLSetDescFields, and SQLSetDescRec calls will fail with SQLSTATE 07006 and the message "Restricted data type attribute violation (the version of SQL Server for this connection does not support table-valued parameters)".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b92d-108">参照</span><span class="sxs-lookup"><span data-stu-id="7b92d-108">See Also</span></span>  
 [<span data-ttu-id="7b92d-109">テーブル値パラメーター &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="7b92d-109">Table-Valued Parameters &#40;ODBC&#41;</span></span>](table-valued-parameters-odbc.md)  
  
  
