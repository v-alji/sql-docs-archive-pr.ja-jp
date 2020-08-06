---
title: アップデートグラムのセキュリティに関する考慮事項 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, updategrams
- security [SQLXML], updategrams
- updategrams [SQLXML], security
ms.assetid: 00dc6cf4-a2e8-4cca-bdd6-d5122102a82d
author: rothja
ms.author: jroth
ms.openlocfilehash: eb0319285e6e8cf6e8b3e70f3eb6b9923de06f55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643736"
---
# <a name="updategram-security-considerations-sqlxml-40"></a><span data-ttu-id="75b27-102">アップデートグラムのセキュリティに関する注意点 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="75b27-102">Updategram Security Considerations (SQLXML 4.0)</span></span>
  <span data-ttu-id="75b27-103">次に、アップデートグラムを使用する場合のセキュリティに関するガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="75b27-103">The following are security guidelines for using updategrams:</span></span>  
  
-   <span data-ttu-id="75b27-104">アップデートグラムを使用してデータを更新する場合、既定のマッピングは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="75b27-104">Avoid using default mapping when you use updategrams to update data.</span></span> <span data-ttu-id="75b27-105">既定のマッピングを使用すると、アップデートグラム内の要素名はテーブル名にマップされ、属性名は列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="75b27-105">When you use default mapping, an element name in an updategram maps to a table name, and an attribute name maps to a column.</span></span> <span data-ttu-id="75b27-106">この方法では、データベース内のデータベース テーブルと列の情報が公開され、セキュリティが脅かされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="75b27-106">This exposes the database table and column information in the database, which can be a potential security risk.</span></span> <span data-ttu-id="75b27-107">代わりに、独自のマッピング スキーマでアップデートグラムの要素および属性をデータベース テーブルおよび列にマップすれば、アップデートグラムの要素および属性には任意の名前を指定でき、スキーマによってこれらの名前のデータベース テーブルおよび列への必要なマッピングが行われます。</span><span class="sxs-lookup"><span data-stu-id="75b27-107">Instead, if you specify a separate mapping schema that maps the elements and attributes in an updategram to the database tables and columns, your updategram element and attribute names can be arbitrary, and the schema does necessary mapping of these names to the database tables and columns.</span></span> <span data-ttu-id="75b27-108">こうすると、アップデートグラムでデータベース情報は公開されません。</span><span class="sxs-lookup"><span data-stu-id="75b27-108">Thus, the database information is not exposed in an updategram.</span></span>  
  
-   <span data-ttu-id="75b27-109">アップデートグラムの作成と実行をユーザーに許可しないでください。</span><span class="sxs-lookup"><span data-stu-id="75b27-109">Do not allow users to create and execute their updategrams.</span></span> <span data-ttu-id="75b27-110">アップデートグラムはテンプレートとしてサーバーに置いておくことをお勧めします。ASP 型のアプリケーションでアップデートグラムを動的に作成すると、データベースのデータが保護されない危険性があります。</span><span class="sxs-lookup"><span data-stu-id="75b27-110">It is recommended having updategrams reside as templates on a server rather than creating them dynamically in ASP-type applications, which could put the data in the database at risk.</span></span> <span data-ttu-id="75b27-111">ユーザーには、アップデートグラムをテンプレートとして提供し、このアップデートグラム経由でのみデータへのアクセスを許可すれば、この危険を回避できます。</span><span class="sxs-lookup"><span data-stu-id="75b27-111">Allowing users to access the data only through the updategrams provided as templates, can eliminate this risk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75b27-112">参照</span><span class="sxs-lookup"><span data-stu-id="75b27-112">See Also</span></span>  
 [<span data-ttu-id="75b27-113">SQLXML 4.0 での、アップデートグラムを使用したデータ変更</span><span class="sxs-lookup"><span data-stu-id="75b27-113">Using Updategrams to Modify Data in SQLXML 4.0</span></span>](../updategrams/using-updategrams-to-modify-data-in-sqlxml-4-0.md)  
  
  
