---
title: テーブル値パラメーター (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, table-valued parameters
- table-valued parameters (OLE DB)
ms.assetid: 4298b73d-615b-4d28-9843-03b4d5fc489e
author: rothja
ms.author: jroth
ms.openlocfilehash: 41d125bcb254125d7f7562ca1873e8af03dab929
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738251"
---
# <a name="table-valued-parameters-ole-db"></a><span data-ttu-id="b4721-102">テーブル値パラメーター (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="b4721-102">Table-Valued Parameters (OLE DB)</span></span>
  <span data-ttu-id="b4721-103">ここでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでのテーブル値パラメーターのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b4721-103">This section describes support for table-valued parameters in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider.</span></span> <span data-ttu-id="b4721-104">追加の概要情報については、「[テーブル値パラメーター &#40;SQL Server Native Client&#41;](../native-client/features/table-valued-parameters-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4721-104">For additional overview information, see [Table-Valued Parameters &#40;SQL Server Native Client&#41;](../native-client/features/table-valued-parameters-sql-server-native-client.md).</span></span> <span data-ttu-id="b4721-105">サンプルについては、「[テーブル値パラメーターの使用 &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4721-105">For a sample, see [Use Table-Valued Parameters &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4721-106">解説</span><span class="sxs-lookup"><span data-stu-id="b4721-106">Remarks</span></span>  
 <span data-ttu-id="b4721-107">現時点では、複数行データを、パラメーター セット (`ICommand::Execute` の DBPARAMS パラメーター) と共にプロシージャのパラメーターとしてサーバーに送信できます。</span><span class="sxs-lookup"><span data-stu-id="b4721-107">Currently, you can send multirow data to the server as parameters to a procedure with parameter sets (the DBPARAMS parameter in `ICommand::Execute`).</span></span> <span data-ttu-id="b4721-108">パラメーター セットを使用する場合、セットの各要素は、個別のリモート プロシージャ コール (RPC) の要求でサーバーに送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4721-108">With parameter sets, every element of the set has to be sent in a separate remote procedure call (RPC) request to the server.</span></span> <span data-ttu-id="b4721-109">テーブル値パラメーターの機能は似ていますが、サーバーとの統合はより緊密になっています。</span><span class="sxs-lookup"><span data-stu-id="b4721-109">Table-valued parameters provide similar functionality, but there is better integration with the server.</span></span> <span data-ttu-id="b4721-110">これにより、RPC 要求の数が減少し、サーバーでセットベースの操作が可能になります。</span><span class="sxs-lookup"><span data-stu-id="b4721-110">This reduces the number of RPC requests and enables set-based operations on the server.</span></span>  
  
 <span data-ttu-id="b4721-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、テーブル値パラメーターが OLE DB `Rowset` オブジェクトとしてサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b4721-111">Table-value parameters are supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider as OLE DB `Rowset` objects.</span></span> <span data-ttu-id="b4721-112">どの `Rowset` オブジェクトも、コンシューマー (つまり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを使用するクライアント アプリケーション) によってテーブル値パラメーターのプレースホルダーとして指定されます。</span><span class="sxs-lookup"><span data-stu-id="b4721-112">Any `Rowset` object could be provided by the consumer (that is, the client application using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider) as a placeholder for table-valued parameter parameters.</span></span> <span data-ttu-id="b4721-113">テーブル値パラメーターは、他の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パラメーターの型と同じように扱われます。</span><span class="sxs-lookup"><span data-stu-id="b4721-113">Table-valued parameters are treated like other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] parameter types.</span></span> <span data-ttu-id="b4721-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって、作成、検索、指定、バインド、およびスキーマのインターフェイスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="b4721-114">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider provides creation, discovery, specification, binding and schema interfaces.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4721-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b4721-115">In This Section</span></span>  
  
-   [<span data-ttu-id="b4721-116">テーブル値パラメーターの行セットの作成</span><span class="sxs-lookup"><span data-stu-id="b4721-116">Table-Valued Parameter Rowset Creation</span></span>](table-valued-parameter-rowset-creation.md)  
  
-   [<span data-ttu-id="b4721-117">テーブル値パラメーターの型の検出</span><span class="sxs-lookup"><span data-stu-id="b4721-117">Table-Valued Parameter Type Discovery</span></span>](../../database-engine/dev-guide/table-valued-parameter-type-discovery.md)  
  
-   [<span data-ttu-id="b4721-118">テーブル値パラメーターを含むコマンドの実行</span><span class="sxs-lookup"><span data-stu-id="b4721-118">Executing Commands Containing Table-Valued Parameters</span></span>](executing-commands-containing-table-valued-parameters.md)  
  
-   [<span data-ttu-id="b4721-119">テーブル値パラメーターへのデータの挿入</span><span class="sxs-lookup"><span data-stu-id="b4721-119">Inserting Data into Table-Valued Parameters</span></span>](inserting-data-into-table-valued-parameters.md)  
  
-   [<span data-ttu-id="b4721-120">OLE DB テーブル値パラメーター向けに変更されたスキーマ行セット</span><span class="sxs-lookup"><span data-stu-id="b4721-120">Schema Rowsets Changed for OLE DB Table-Valued Parameters</span></span>](schema-rowsets-changed-for-ole-db-table-valued-parameters.md)  
  
-   [<span data-ttu-id="b4721-121">OLE DB テーブル値パラメーターの型のサポート</span><span class="sxs-lookup"><span data-stu-id="b4721-121">OLE DB Table-Valued Parameter Type Support</span></span>](ole-db-table-valued-parameter-type-support.md)  
  
-   [<span data-ttu-id="b4721-122">OLE DB テーブル値パラメーターの型のサポート (メソッド)</span><span class="sxs-lookup"><span data-stu-id="b4721-122">OLE DB Table-Valued Parameter Type Support &#40;Methods&#41;</span></span>](ole-db-table-valued-parameter-type-support-methods.md)  
  
-   [<span data-ttu-id="b4721-123">OLE DB テーブル値パラメーターの型のサポート (プロパティ)</span><span class="sxs-lookup"><span data-stu-id="b4721-123">OLE DB Table-Valued Parameter Type Support &#40;Properties&#41;</span></span>](ole-db-table-valued-parameter-type-support-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="b4721-124">参照</span><span class="sxs-lookup"><span data-stu-id="b4721-124">See Also</span></span>  
 <span data-ttu-id="b4721-125">[SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="b4721-125">[SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md) </span></span>  
 [<span data-ttu-id="b4721-126">テーブル値パラメーターの使用 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="b4721-126">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
