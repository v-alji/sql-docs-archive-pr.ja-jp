---
title: カーソルプログラミングの詳細 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- ODBC cursors, programming
- cursors [ODBC], programming
ms.assetid: 6bae29c4-7f49-419c-8712-90db734f992e
author: rothja
ms.author: jroth
ms.openlocfilehash: 4108e195c16d321578a70852dd990f4f8d658832
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634519"
---
# <a name="cursor-programming-details-odbc"></a><span data-ttu-id="1f407-102">カーソル プログラミングの詳細 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="1f407-102">Cursor Programming Details (ODBC)</span></span>
  <span data-ttu-id="1f407-103">適切なカーソルの種類を選択することで、アプリケーションのパフォーマンスを向上することができます。</span><span class="sxs-lookup"><span data-stu-id="1f407-103">Choosing the correct cursor type can improve application performance.</span></span> <span data-ttu-id="1f407-104">ただし、ある条件下では、要求したカーソルの種類でサポートされていない SQL ステートメントを実行すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によりカーソルの種類が暗黙的に変換されることがあります。</span><span class="sxs-lookup"><span data-stu-id="1f407-104">Under certain conditions, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] may implicitly convert a cursor type when you execute an SQL statement that is not supported by the cursor type you requested.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1f407-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1f407-105">In This Section</span></span>  
  
-   [<span data-ttu-id="1f407-106">ODBC&#41;&#40;の暗黙的なカーソル変換</span><span class="sxs-lookup"><span data-stu-id="1f407-106">Implicit Cursor Conversions &#40;ODBC&#41;</span></span>](implicit-cursor-conversions-odbc.md)  
  
-   [<span data-ttu-id="1f407-107">Autofetch と ODBC カーソルの併用</span><span class="sxs-lookup"><span data-stu-id="1f407-107">Using Autofetch with ODBC Cursors</span></span>](using-autofetch-with-odbc-cursors.md)  
  
-   [<span data-ttu-id="1f407-108">ODBC&#41;&#40;高速順方向専用カーソル</span><span class="sxs-lookup"><span data-stu-id="1f407-108">Fast Forward-Only Cursors &#40;ODBC&#41;</span></span>](fast-forward-only-cursors-odbc.md)  
  
## <a name="see-also"></a><span data-ttu-id="1f407-109">参照</span><span class="sxs-lookup"><span data-stu-id="1f407-109">See Also</span></span>  
 [<span data-ttu-id="1f407-110">ODBC&#41;&#40;カーソルの使用</span><span class="sxs-lookup"><span data-stu-id="1f407-110">Using Cursors &#40;ODBC&#41;</span></span>](../using-cursors-odbc.md)  
  
  
