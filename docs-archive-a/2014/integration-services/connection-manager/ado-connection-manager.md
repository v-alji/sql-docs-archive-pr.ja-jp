---
title: ADO 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], ADO
- connection managers [Integration Services], ADO
- ADO connection manager [Integration Services]
ms.assetid: 490418bc-5ef1-41b8-a9c8-de38aa96e0f6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fb4b667733f81eebbaf2b6a2ab9b205c09fe2c66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644109"
---
# <a name="ado-connection-manager"></a><span data-ttu-id="43f76-102">ADO 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="43f76-102">ADO Connection Manager</span></span>
  <span data-ttu-id="43f76-103">ADO 接続マネージャーを使用すると、レコードセットなどの ADO (ActiveX データ オブジェクト) オブジェクトにパッケージを接続できます。</span><span class="sxs-lookup"><span data-stu-id="43f76-103">An ADO connection manager enables a package to connect to ActiveX Data Objects (ADO) objects, such as a recordset.</span></span> <span data-ttu-id="43f76-104">この接続マネージャーは、通常、Microsoft Visual Basic 6.0 などの以前のバージョンの言語で記述されたカスタム タスクや、ADO を使用してデータ ソースに接続する既存のアプリケーションの一部のカスタム タスクで使用されます。</span><span class="sxs-lookup"><span data-stu-id="43f76-104">This connection manager is typically used in custom tasks written in an earlier version of a language, such as Microsoft Visual Basic 6.0, or in custom tasks that are part of an existing application that uses ADO to connect to a data source.</span></span>  
  
 <span data-ttu-id="43f76-105">Ado 接続マネージャーをパッケージに追加すると、は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 実行時に ado 接続を解決する接続マネージャーを作成し、接続マネージャーのプロパティを設定して、接続マネージャーをパッケージのコレクションに追加し `Connections` ます。</span><span class="sxs-lookup"><span data-stu-id="43f76-105">When you add an ADO connection manager to a package, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an ADO connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="43f76-106">接続マネージャーの `ConnectionManagerType` プロパティは、`ADO` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="43f76-106">The `ConnectionManagerType` property of the connection manager is set to `ADO`.</span></span>  
  
## <a name="troubleshooting-the-ado-connection-manager"></a><span data-ttu-id="43f76-107">ADO 接続マネージャーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="43f76-107">Troubleshooting the ADO Connection Manager</span></span>  
 <span data-ttu-id="43f76-108">ADO 接続マネージャーに読み込まれると、特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日付データ型は次の表に示す結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="43f76-108">When being read by an ADO connection manager, certain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date data types will generate the results shown in the following table.</span></span>  
  
|<span data-ttu-id="43f76-109">SQL Server データ型</span><span class="sxs-lookup"><span data-stu-id="43f76-109">SQL Server Data type</span></span>|<span data-ttu-id="43f76-110">結果</span><span class="sxs-lookup"><span data-stu-id="43f76-110">Result</span></span>|  
|--------------------------|------------|  
|<span data-ttu-id="43f76-111">`time`, `datetimeoffset`</span><span class="sxs-lookup"><span data-stu-id="43f76-111">`time`, `datetimeoffset`</span></span>|<span data-ttu-id="43f76-112">パッケージがパラメーター化 SQL コマンドを使用していない場合、パッケージは失敗します。</span><span class="sxs-lookup"><span data-stu-id="43f76-112">The package fails unless the package uses parameterized SQL commands.</span></span> <span data-ttu-id="43f76-113">パラメーター化 SQL コマンドを使用するには、パッケージで SQL 実行タスクを使用します。</span><span class="sxs-lookup"><span data-stu-id="43f76-113">To use parameterized SQL commands, use the Execute SQL Task in your package.</span></span> <span data-ttu-id="43f76-114">詳細については、「 [SQL 実行タスク](../control-flow/execute-sql-task.md) 」と「 [SQL 実行タスクのパラメーターとリターン コード](../parameters-and-return-codes-in-the-execute-sql-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43f76-114">For more information, see [Execute SQL Task](../control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>|  
|`datetime2`|<span data-ttu-id="43f76-115">ADO 接続マネージャーは、ミリ秒の値を切り捨てます。</span><span class="sxs-lookup"><span data-stu-id="43f76-115">The ADO connection manager truncates the millisecond value.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="43f76-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型の詳細とそれを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] データ型にマッピングする方法については、「[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)」と「[Integration Services のデータ型](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43f76-116">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types and how they map to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) and [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="configuring-the-ado-connection-manager"></a><span data-ttu-id="43f76-117">ADO 接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="43f76-117">Configuring the ADO Connection Manager</span></span>  
 <span data-ttu-id="43f76-118">ADO 接続マネージャーは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="43f76-118">You can configure an ADO connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="43f76-119">選択したプロバイダーの要件を満たすように構成された、特定の接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="43f76-119">Provide a specific connection string configured to meet the requirements of the selected provider.</span></span>  
  
-   <span data-ttu-id="43f76-120">プロパイダによっては、接続先のデータ ソースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="43f76-120">Depending on the provider, include the name of the data source to connect to.</span></span>  
  
-   <span data-ttu-id="43f76-121">選択したプロバイダーに適したセキュリティ資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="43f76-121">Provide security credentials as appropriate for the selected provider.</span></span>  
  
-   <span data-ttu-id="43f76-122">接続マネージャーから作成される接続を、実行時に保持するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="43f76-122">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
 <span data-ttu-id="43f76-123">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="43f76-123">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="43f76-124">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="43f76-124">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   <span data-ttu-id="43f76-125">[[OLE DB 接続マネージャーの構成]](ole-db-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="43f76-125">[Configure OLE DB Connection Manager](ole-db-connection-manager.md)</span></span>  
  
 <span data-ttu-id="43f76-126">プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。</span><span class="sxs-lookup"><span data-stu-id="43f76-126">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f76-127">参照</span><span class="sxs-lookup"><span data-stu-id="43f76-127">See Also</span></span>  
 [<span data-ttu-id="43f76-128">Integration Services &#40;SSIS&#41; の接続</span><span class="sxs-lookup"><span data-stu-id="43f76-128">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
