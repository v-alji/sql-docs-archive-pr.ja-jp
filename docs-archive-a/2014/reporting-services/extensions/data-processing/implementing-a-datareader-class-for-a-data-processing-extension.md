---
title: データ処理拡張機能の DataReader クラスの実装 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], data readers
- data readers [Reporting Services]
- DataReader class
- read-only data
ms.assetid: 23e286e7-6074-4fbe-be29-203420d6c3d0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7c9e55741c72d624b7149435ced90550135d8b4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741593"
---
# <a name="implementing-a-datareader-class-for-a-data-processing-extension"></a><span data-ttu-id="8ed85-102">データ処理拡張機能の DataReader クラスの実装</span><span class="sxs-lookup"><span data-stu-id="8ed85-102">Implementing a DataReader Class for a Data Processing Extension</span></span>
  <span data-ttu-id="8ed85-103">クライアントは **DataReader** オブジェクトを使用して、読み取り専用、順方向専用のデータ ストリームをデータ ソースから取得できます。</span><span class="sxs-lookup"><span data-stu-id="8ed85-103">The **DataReader** object enables a client to retrieve a read-only, forward-only stream of data from a data source.</span></span> <span data-ttu-id="8ed85-104">クエリを実行すると結果が返され、結果は **DataReader** クラスの **Read** メソッドを使用して要求するまではクライアントのネットワーク バッファーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="8ed85-104">Results are returned as the query executes and are stored in the network buffer on the client until you request them using the **Read** method of the **DataReader** class.</span></span> <span data-ttu-id="8ed85-105">**DataReader** クラスを作成するには、<xref:Microsoft.ReportingServices.DataProcessing.IDataReader> を実装し、必要に応じて <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension> を実装します。</span><span class="sxs-lookup"><span data-stu-id="8ed85-105">To create a **DataReader** class, implement <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> and optionally implement <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension>.</span></span> <span data-ttu-id="8ed85-106">**DataReader** オブジェクトを使用すると、アプリケーションのパフォーマンスが向上します。これは、クエリの結果全体が返されるまで待機するのではなく、データが使用可能になりしだい取得することと、メモリに一度に 1 行のみが格納されるため (既定)、システムのオーバーヘッドが小さくなることにより実現します。</span><span class="sxs-lookup"><span data-stu-id="8ed85-106">Using a **DataReader** object increases application performance both by retrieving data as soon as it is available, rather than waiting for the entire results of the query to be returned, and (by default) storing only one row at a time in memory, reducing system overhead.</span></span>  
  
 <span data-ttu-id="8ed85-107">**Command** クラスのインスタンスを作成した後に、**Command.ExecuteReader** を呼び出してデータ ソースから行を取得することによって、**DataReader** オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8ed85-107">After creating an instance of your **Command** class, you create a **DataReader** object by calling **Command.ExecuteReader** to retrieve rows from the data source.</span></span> <span data-ttu-id="8ed85-108">**DataReader** の実装によって、コマンドの実行により取得した結果セットへの順方向専用アクセス、および各行内の列型、名前、および値へのアクセスという 2 つの基本機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="8ed85-108">The **DataReader** implementation must provide two basic capabilities: forward-only access over the result sets obtained by executing a command and access to the column types, names, and values within each row.</span></span> <span data-ttu-id="8ed85-109">クライアントは **DataReader** オブジェクトの **Read** メソッドを使用して、クエリの結果から行を取得します。</span><span class="sxs-lookup"><span data-stu-id="8ed85-109">Clients use the **Read** method of the **DataReader** object to obtain a row from the results of the query.</span></span>  
  
 <span data-ttu-id="8ed85-110">レポート デザイナーでは、**DataReader** オブジェクトを使用して、フィールドの一覧の他に結果セットに関するスキーマ情報も取得します。</span><span class="sxs-lookup"><span data-stu-id="8ed85-110">In Report Designer, your **DataReader** object is used to retrieve a list of fields as well as schema information about the result set.</span></span> <span data-ttu-id="8ed85-111">このためには、<xref:Microsoft.ReportingServices.DataProcessing.IDataReader> インターフェイスの **GetName**、**GetValue**、**GetFieldType、** および **GetOrdinal** の各メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="8ed85-111">This is accomplished by implementing the **GetName**, **GetValue**, **GetFieldType,** and **GetOrdinal** methods of the <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> interface.</span></span>  
  
 <span data-ttu-id="8ed85-112"><xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension> インターフェイスでは、結果セットに関する特定の集計情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8ed85-112">The <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension> interface allows you to supply specific aggregation information about your result set.</span></span> <span data-ttu-id="8ed85-113">**DataReader** クラス実装の例については、「[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services 製品サンプル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ed85-113">For a sample **DataReader** class implementation, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ed85-114">参照</span><span class="sxs-lookup"><span data-stu-id="8ed85-114">See Also</span></span>  
 <span data-ttu-id="8ed85-115">[Reporting Services の拡張機能](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="8ed85-115">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="8ed85-116">[データ処理拡張機能の実装](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="8ed85-116">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="8ed85-117">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="8ed85-117">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
