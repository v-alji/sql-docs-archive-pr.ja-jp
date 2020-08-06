---
title: 大きな XML スキーマ コレクションとメモリ不足状態 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- out-of-memory conditions
- XML schema collections [SQL Server], large
ms.assetid: 29b9d839-aaaf-48fb-be17-840c751f36f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 8443207bbbdff5db7e54d61fcebabe70e34cc540
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743049"
---
# <a name="large-xml-schema-collections-and-out-of-memory-conditions"></a><span data-ttu-id="2d700-102">大きな XML スキーマ コレクションとメモリ不足状態</span><span class="sxs-lookup"><span data-stu-id="2d700-102">Large XML Schema Collections and Out-of-Memory Conditions</span></span>
  <span data-ttu-id="2d700-103">大きな XML スキーマ コレクションで組み込み XML_SCHEMA_NAMESPACE() 関数を呼び出しているとき、または大きな XML スキーマ コレクションを削除するときに、メモリが不足することがあります。</span><span class="sxs-lookup"><span data-stu-id="2d700-103">During a call to the built-in XML_SCHEMA_NAMESPACE() function on a large XML schema collection, or when you try to drop large XML schema collections, an out-of-memory condition may occur.</span></span> <span data-ttu-id="2d700-104">次に示すのは、このような状態に対処する際に使用できる解決策です。</span><span class="sxs-lookup"><span data-stu-id="2d700-104">The following are solutions you can use to handle this:</span></span>  
  
-   <span data-ttu-id="2d700-105">システムの負荷が低い場合は、DROP_XML_SCHEMA_COLLECTION コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="2d700-105">When the system load is light, use the DROP_XML_SCHEMA_COLLECTION command.</span></span> <span data-ttu-id="2d700-106">この操作が失敗する場合は、ALTER DATABASE ステートメントを使用し、DROP XML SCHEMA COLLECTION を再試行してデータベースをシングル ユーザー モードにします。</span><span class="sxs-lookup"><span data-stu-id="2d700-106">If this fails, put the database in single-user mode by using the ALTER DATABASE statement and trying DROP XML SCHEMA COLLECTION again.</span></span> <span data-ttu-id="2d700-107">XML スキーマ コレクションが **master**、 **model**、または **tempdb**に存在する場合は、シングル ユーザー モードにするためにサーバーを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d700-107">If the XML schema collection exists in **master**, **model**, or **tempdb**, a server restart is required for single-user mode.</span></span>  
  
-   <span data-ttu-id="2d700-108">XML_SCHEMA_NAMESPACE を呼び出す場合、単一の XML スキーマ名前空間の取得、システムの負荷低下時の呼び出し、またはシングル ユーザー モードでの呼び出しを試行することができます。</span><span class="sxs-lookup"><span data-stu-id="2d700-108">When you call the XML_SCHEMA_NAMESPACE, you can try to retrieve a single XML schema namespace, you can try the call when the system load is lighter, or you can try the call in single-user mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d700-109">参照</span><span class="sxs-lookup"><span data-stu-id="2d700-109">See Also</span></span>  
 [<span data-ttu-id="2d700-110">サーバー上の XML スキーマ コレクションの要件と制限</span><span class="sxs-lookup"><span data-stu-id="2d700-110">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
