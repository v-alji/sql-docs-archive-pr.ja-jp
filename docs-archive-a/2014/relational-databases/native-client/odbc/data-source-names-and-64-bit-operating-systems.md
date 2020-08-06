---
title: データソース名と64ビットオペレーティングシステム |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
author: rothja
ms.author: jroth
ms.openlocfilehash: ae31584ca3c076919f688d1ef9bdef80706c6940
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633816"
---
# <a name="data-source-names-and-64-bit-operating-systems"></a><span data-ttu-id="ce2fb-102">データ ソース名と 64 ビット オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="ce2fb-102">Data Source Names and 64-Bit Operating Systems</span></span>
  <span data-ttu-id="ce2fb-103">アプリケーションを 64 ビット オペレーティング システムで 32 ビット アプリケーションとしてビルドして実行する場合、%windir%\SysWOW64\odbcad32.exe の ODBC アドミニストレーターを使用して ODBC データ ソースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-103">To build and run an application as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce2fb-104">解説</span><span class="sxs-lookup"><span data-stu-id="ce2fb-104">Remarks</span></span>  
 <span data-ttu-id="ce2fb-105">64 ビットの Windows オペレーティング システムには、2 つの odbcad32.exe ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-105">A 64-bit Windows operating system has two odbcad32.exe files:</span></span>  
  
-   <span data-ttu-id="ce2fb-106">%SystemRoot%\system32\odbcad32.exe は、64 ビット アプリケーションのデータ ソース名の作成と保持に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-106">%SystemRoot%\system32\odbcad32.exe is used to create and maintain data source names for 64-bit applications.</span></span>  
  
-   <span data-ttu-id="ce2fb-107">%SystemRoot%\SysWOW64\odbcad32.exe は、64 ビット オペレーティング システムで実行される 32 ビット アプリケーションなど、32 ビット アプリケーションのデータ ソース名の作成と保持に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ce2fb-107">%SystemRoot%\SysWOW64\odbcad32.exe is used to create and maintain data source names for 32-bit applications, including 32-bit applications that run on 64-bit operating systems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce2fb-108">参照</span><span class="sxs-lookup"><span data-stu-id="ce2fb-108">See Also</span></span>  
 [<span data-ttu-id="ce2fb-109">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="ce2fb-109">SQL Server Native Client &#40;ODBC&#41;</span></span>](sql-server-native-client-odbc.md)  
  
  
