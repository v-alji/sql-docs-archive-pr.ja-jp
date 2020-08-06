---
title: ユーザー定義データ型 (UDT) の FOR XML サポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- UDTs [SQL Server], XML
- user-defined types [SQL Server], XML
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
author: rothja
ms.author: jroth
ms.openlocfilehash: b668ad2da13fdfc880ab26cb2b2759ff3693f7d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743086"
---
# <a name="for-xml-support-for-the-user-defined-data-types-udt"></a><span data-ttu-id="e89cd-102">ユーザー定義データ型 (UDT) の FOR XML サポート</span><span class="sxs-lookup"><span data-stu-id="e89cd-102">FOR XML Support for the User-Defined Data Types (UDT)</span></span>
  <span data-ttu-id="e89cd-103">FOR XML は、共通言語ランタイム (CLR) のユーザー定義データ型 (UDT) をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e89cd-103">FOR XML does not support common language runtime (CLR) user-defined data types (UDTs).</span></span>  
  
 <span data-ttu-id="e89cd-104">CLR のユーザー定義データ型で FOR XML を使用するには、そのデータ型で XML シリアル化を指定して、FOR XML SELECT 句で XML への明示的なキャストを使用します。</span><span class="sxs-lookup"><span data-stu-id="e89cd-104">To use FOR XML with CLR user-defined data types, make sure that the data type has an XML serialization, and use an explicit cast to XML in the FOR XML select clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e89cd-105">参照</span><span class="sxs-lookup"><span data-stu-id="e89cd-105">See Also</span></span>  
 [<span data-ttu-id="e89cd-106">各種 SQL Server データ型の FOR XML サポート</span><span class="sxs-lookup"><span data-stu-id="e89cd-106">FOR XML Support for Various SQL Server Data Types</span></span>](for-xml-support-for-various-sql-server-data-types.md)  
  
  
