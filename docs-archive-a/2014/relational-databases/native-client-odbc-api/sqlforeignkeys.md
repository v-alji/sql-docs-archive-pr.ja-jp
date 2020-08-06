---
title: SQLForeignKeys |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLForeignKeys function
ms.assetid: 6c01ce0d-30d7-4c86-8705-3ab254d8a845
author: rothja
ms.author: jroth
ms.openlocfilehash: a61e80867abb8ecb4d2628b74dc9956051c8e4ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634536"
---
# <a name="sqlforeignkeys"></a><span data-ttu-id="892d3-102">SQLForeignKeys</span><span class="sxs-lookup"><span data-stu-id="892d3-102">SQLForeignKeys</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="892d3-103">では、外部キー制約メカニズムによってカスケード更新とカスケード削除がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="892d3-103">supports cascading updates and deletes through the foreign key constraint mechanism.</span></span> <span data-ttu-id="892d3-104">FOREIGN KEY 制約の ON UPDATE 句や ON DELETE 句で CASCADE オプションが指定されている場合、UPDATE_RULE 列や DELETE_RULE 列に対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から SQL_CASCADE が返されます。</span><span class="sxs-lookup"><span data-stu-id="892d3-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] returns SQL_CASCADE for UPDATE_RULE and/or DELETE_RULE columns if CASCADE option is specified on the ON UPDATE and/or ON DELETE clause of the FOREIGN KEY constraints.</span></span> <span data-ttu-id="892d3-105">FOREIGN KEY 制約の ON UPDATE 句や ON DELETE 句で NO ACTION オプションが指定されている場合は、UPDATE_RULE 列や DELETE_RULE 列に対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から SQL_NO_ACTION が返されます。</span><span class="sxs-lookup"><span data-stu-id="892d3-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] returns SQL_NO_ACTION for UPDATE_RULE and/or DELETE_RULE columns if NO ACTION option is specified on the ON UPDATE and/or ON DELETE clause of the FOREIGN KEY constraints.</span></span>  
  
 <span data-ttu-id="892d3-106">**SQLForeignKeys**パラメーターに無効な値が含まれている場合、 **SQLForeignKeys**は実行時に SQL_SUCCESS を返します。</span><span class="sxs-lookup"><span data-stu-id="892d3-106">When invalid values are present in any **SQLForeignKeys** parameter, **SQLForeignKeys** returns SQL_SUCCESS on execution.</span></span> <span data-ttu-id="892d3-107">これらのパラメーターで無効な値が使用されている場合、 **Sqlfetch**は SQL_NO_DATA を返します。</span><span class="sxs-lookup"><span data-stu-id="892d3-107">**SQLFetch** returns SQL_NO_DATA when invalid values are used in these parameters.</span></span>  
  
 <span data-ttu-id="892d3-108">**SQLForeignKeys**は、静的サーバーカーソルで実行できます。</span><span class="sxs-lookup"><span data-stu-id="892d3-108">**SQLForeignKeys** can be executed on a static server cursor.</span></span> <span data-ttu-id="892d3-109">更新可能なカーソル (動的カーソルまたはキーセットカーソル) で**SQLForeignKeys**を実行しようとすると、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO が返されます。</span><span class="sxs-lookup"><span data-stu-id="892d3-109">An attempt to execute **SQLForeignKeys** on an updatable (dynamic or keyset) cursor returns SQL_SUCCESS_WITH_INFO indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="892d3-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC ドライバーでは、 *FKCatalogName*パラメーターと*PKCatalogName* Linked_Server_Name パラメーターの2つの部分で構成される名前を使用して、リンクサーバー上のテーブルのレポート情報をサポートしています。 *Catalog_Name*を参照してください。</span><span class="sxs-lookup"><span data-stu-id="892d3-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports reporting information for tables on linked servers by accepting a two-part name for the *FKCatalogName* and *PKCatalogName* parameters: *Linked_Server_Name.Catalog_Name*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="892d3-111">参照</span><span class="sxs-lookup"><span data-stu-id="892d3-111">See Also</span></span>  
 <span data-ttu-id="892d3-112">[SQLForeignKeys 関数](https://go.microsoft.com/fwlink/?LinkId=59344) </span><span class="sxs-lookup"><span data-stu-id="892d3-112">[SQLForeignKeys Function](https://go.microsoft.com/fwlink/?LinkId=59344) </span></span>  
 [<span data-ttu-id="892d3-113">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="892d3-113">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
