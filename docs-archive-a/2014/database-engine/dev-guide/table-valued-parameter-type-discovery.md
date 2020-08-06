---
title: テーブル値パラメーターの型探索 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ab8d837e4ddf74256e4bae70f772557ec8ff67f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716694"
---
# <a name="table-valued-parameter-type-discovery"></a><span data-ttu-id="8863c-102">テーブル値パラメーターの型の検出</span><span class="sxs-lookup"><span data-stu-id="8863c-102">Table-Valued Parameter Type Discovery</span></span>
  <span data-ttu-id="8863c-103">コンシューマー (つまり、Native Client OLE DB プロバイダーを使用するクライアントアプリケーション) は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コマンドテキストが OLE DB プロバイダーに与えられていれば、各コマンドパラメーターの型を検出できます。</span><span class="sxs-lookup"><span data-stu-id="8863c-103">The consumer-that is, the client application using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Provider-can discover the type of each command parameter if the command text has been given to the OLE DB Provider.</span></span> <span data-ttu-id="8863c-104">テーブル値パラメーターの型がわかったら、コンシューマーはテーブル値パラメーターの個別の列ごとにメタデータ情報を検出できます。</span><span class="sxs-lookup"><span data-stu-id="8863c-104">After the type of a table-valued parameter is known, the consumer can discover the metadata information for each individual column of the table-valued parameter.</span></span>  
  
 <span data-ttu-id="8863c-105">プロシージャ パラメーターの型情報は、ほとんどのパラメーター型について ICommandWithParameters::GetParameterInfo でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="8863c-105">The type information of procedure parameters is supported by ICommandWithParameters::GetParameterInfo for most parameter types.</span></span> <span data-ttu-id="8863c-106">以降では [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 、ユーザー定義型とデータ型の導入により、 `xml` getparameterinfo メソッドは、ICommandWithParameters を介してユーザー定義型情報 (名前、スキーマ、およびカタログ) を提供できなかったため、この目的には不十分でした。</span><span class="sxs-lookup"><span data-stu-id="8863c-106">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], with the introduction of user-defined types and the `xml` data type, the GetParameterInfo method was not sufficient for this purpose because it was not possible to provide user-defined type information (name, schema, and catalog) through ICommandWithParameters.</span></span> <span data-ttu-id="8863c-107">拡張された型情報を提供するために、新しいインターフェイス ISSCommandWithParameters が定義されました。</span><span class="sxs-lookup"><span data-stu-id="8863c-107">A new interface, ISSCommandWithParameters, was defined to provide extended type information.</span></span>  
  
 <span data-ttu-id="8863c-108">テーブル値パラメーターの場合は、ISSCommandWithParameters インターフェイスを使用して、詳細情報も検出します。</span><span class="sxs-lookup"><span data-stu-id="8863c-108">For table-valued parameters, you also use the ISSCommandWithParameters interface to discover detailed information.</span></span> <span data-ttu-id="8863c-109">クライアントは、コマンド オブジェクトを準備した後、ISSCommandWithParameters::GetParameterInfo を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8863c-109">The client calls ISSCommandWithParameters::GetParameterInfo after preparing the command object.</span></span> <span data-ttu-id="8863c-110">テーブル値パラメーターでは、DBPARAMINFO 構造体の *wType* メンバーが、プロバイダーによって DBTYPE_TABLE に設定されます。</span><span class="sxs-lookup"><span data-stu-id="8863c-110">For table-valued parameters, the *wType* member of the DBPARAMINFO structure is set to DBTYPE_TABLE by the provider.</span></span> <span data-ttu-id="8863c-111">DBPARAMINFO 構造体の *ulParamSize* フィールドの値は ~0 です。</span><span class="sxs-lookup"><span data-stu-id="8863c-111">The *ulParamSize* field of DBPARAMINFO structure has a value of ~0.</span></span>  
  
 <span data-ttu-id="8863c-112">コンシューマーは、次に ISSCommandWithParameters::GetParameterProperties を使用して、追加のプロパティ (テーブル値パラメーターの型のカタログ名、テーブル値パラメーターの型のスキーマ名、テーブル値パラメーターの型名、列の順序、および既定の列) を要求します。</span><span class="sxs-lookup"><span data-stu-id="8863c-112">The consumer would then request additional properties (table-valued parameter type catalog name, table-valued parameter type schema name, table-valued parameter type name, column ordering, and default columns) by using ISSCommandWithParameters::GetParameterProperties.</span></span>  
  
 <span data-ttu-id="8863c-113">型名がわかったら、コンシューマーは個々の列情報を取得するために、IOpenRowset::OpenRowset を呼び出すか、テーブル値パラメーターの型名をテーブル名として指定して、DBSCHEMA_TABLE_TYPE_COLUMNS 行セットを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8863c-113">After the type name is known, to retrieve the individual column information the consumer must either call IOpenRowset::OpenRowsetor obtain the DBSCHEMA_TABLE_TYPE_COLUMNS rowset by specifying the table-valued parameter type name as the table name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8863c-114">参照</span><span class="sxs-lookup"><span data-stu-id="8863c-114">See Also</span></span>  
 <span data-ttu-id="8863c-115">[テーブル値パラメーター &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="8863c-115">[Table-Valued Parameters &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="8863c-116">テーブル値パラメーターの使用 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8863c-116">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
