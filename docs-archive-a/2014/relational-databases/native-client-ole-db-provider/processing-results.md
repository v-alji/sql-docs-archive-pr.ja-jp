---
title: 結果の処理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, results processing
- OLE DB, processing results
- rowsets [SQL Server], results processing
- results [SQL Server Native Client]
ms.assetid: 20887ac4-f649-4e7f-92e6-f929e2e70952
author: rothja
ms.author: jroth
ms.openlocfilehash: b9e5bf00b4d2e554536c9f2ba1a328390b93a8a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643793"
---
# <a name="processing-results"></a><span data-ttu-id="7e63e-102">結果の処理</span><span class="sxs-lookup"><span data-stu-id="7e63e-102">Processing Results</span></span>
  <span data-ttu-id="7e63e-103">コマンドの実行、またはプロバイダーからの行セット オブジェクトの直接生成のいずれかによって行セット オブジェクトを作成する場合、コンシューマーはその行セット内のデータにアクセスして、データを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e63e-103">If a rowset object is produced by either the execution of a command or the generation of a rowset object directly from the provider, the consumer needs to retrieve and access data in the rowset.</span></span>  
  
 <span data-ttu-id="7e63e-104">行セットは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが表形式でデータを公開できるようにするための重要な機能を持つオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="7e63e-104">Rowsets are the central objects that enable the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider to expose data in tabular form.</span></span> <span data-ttu-id="7e63e-105">概念的には、行セットは行の集まりを表し、各行には列データが格納されています。</span><span class="sxs-lookup"><span data-stu-id="7e63e-105">Conceptually, a rowset is a set of rows in which each row has column data.</span></span> <span data-ttu-id="7e63e-106">行セット オブジェクトでは、**IRowset** (行セットから順番に行をフェッチするメソッドを含みます)、**IAccessor** (コンシューマーのプログラム変数に表形式のデータをバインドする方法を指定する一連の列バインドの定義を許可します)、**IColumnsInfo** (行セット内の列に関する情報を提供します)、**IRowsetInfo** (行セットに関する情報を提供します) などのインターフェイスが公開されます。</span><span class="sxs-lookup"><span data-stu-id="7e63e-106">A rowset object exposes interfaces such as **IRowset** (contains methods for fetching rows from the rowset sequentially), **IAccessor** (permits the definition of a group of column bindings describing the way tabular data is bound to consumer program variables), **IColumnsInfo** (provides information about columns in the rowset), and **IRowsetInfo** (provides information about rowset).</span></span>  
  
 <span data-ttu-id="7e63e-107">コンシューマーは、**IRowset::GetData** メソッドを呼び出して、データ行を行セットからバッファーに取得できます。</span><span class="sxs-lookup"><span data-stu-id="7e63e-107">A consumer can call the **IRowset::GetData** method to retrieve a row of data from the rowset into a buffer.</span></span> <span data-ttu-id="7e63e-108">**GetData** を呼び出す前に、DBBINDING 構造体のセットを使用してバッファーを記述します。</span><span class="sxs-lookup"><span data-stu-id="7e63e-108">Before **GetData** is called, the consumer describes the buffer using a set of DBBINDING structures.</span></span> <span data-ttu-id="7e63e-109">各バインドは、行セット内の列をコンシューマーのバッファーに格納する方法を記述するもので、次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7e63e-109">Each binding describes how a column in a rowset is stored in a consumer buffer and contains the following:</span></span>  
  
-   <span data-ttu-id="7e63e-110">バインドが適用される列 (パラメーター) の序数</span><span class="sxs-lookup"><span data-stu-id="7e63e-110">Ordinal of the column (or parameter) to which the binding applies.</span></span>  
  
-   <span data-ttu-id="7e63e-111">バインドされる内容 (データ値、データの長さ、バインドの状態など) に関する情報</span><span class="sxs-lookup"><span data-stu-id="7e63e-111">Information about what is bound (for example, data value, length of the data, and its binding status).</span></span>  
  
-   <span data-ttu-id="7e63e-112">バッファー内の各部分へのオフセットに関する情報</span><span class="sxs-lookup"><span data-stu-id="7e63e-112">Information about what is offset in the buffer to each of these parts.</span></span>  
  
-   <span data-ttu-id="7e63e-113">コンシューマーのバッファー内でのデータ値の長さと型</span><span class="sxs-lookup"><span data-stu-id="7e63e-113">Length and type of the data values as they exist in the consumer buffer.</span></span>  
  
 <span data-ttu-id="7e63e-114">プロバイダーはデータを取得するときに、各バインドの情報を使用してコンシューマーのバッファーからデータを取得する位置と方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="7e63e-114">When getting the data, the provider uses information in each binding to determine where and how to retrieve data from the consumer buffer.</span></span> <span data-ttu-id="7e63e-115">また、コンシューマーのバッファーにデータを設定するときに、各バインドの情報を使用してコンシューマーのバッファー内にあるデータを返す位置と方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="7e63e-115">When setting data in the consumer buffer, the provider uses information in each binding to determine where and how to return data in the consumer's buffer.</span></span>  
  
 <span data-ttu-id="7e63e-116">DBBINDING 構造体を指定したら、アクセサーを作成 (**IAccessor::CreateAccessor**) します。</span><span class="sxs-lookup"><span data-stu-id="7e63e-116">After the DBBINDING structures are specified, an accessor is created (**IAccessor::CreateAccessor**).</span></span> <span data-ttu-id="7e63e-117">バインドの集まりであるアクセサーは、コンシューマーのバッファー内のデータを取得または設定するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="7e63e-117">An accessor is a collection of bindings and is used to get or set the data in the consumer buffer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e63e-118">参照</span><span class="sxs-lookup"><span data-stu-id="7e63e-118">See Also</span></span>  
 <span data-ttu-id="7e63e-119">[SQL Server Native Client OLE DB プロバイダーアプリケーションの作成](creating-a-sql-server-native-client-ole-db-provider-application.md) </span><span class="sxs-lookup"><span data-stu-id="7e63e-119">[Creating a SQL Server Native Client OLE DB Provider Application](creating-a-sql-server-native-client-ole-db-provider-application.md) </span></span>  
 [<span data-ttu-id="7e63e-120">OLE DB の使用法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="7e63e-120">OLE DB How-to Topics</span></span>](../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
