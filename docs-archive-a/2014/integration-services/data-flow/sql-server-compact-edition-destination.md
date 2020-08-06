---
title: SQL Server Compact Edition 変換先 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlservercompactdest.f1
helpviewer_keywords:
- destinations [Integration Services], SQL Server Compact
- SQL Server Compact, destination
- inserting data
ms.assetid: 697742ba-cc14-414d-8187-1845ad0dd99b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bfeb0bfce54c9ebefb5c526656be6b736dc0d82b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644074"
---
# <a name="sql-server-compact-edition-destination"></a><span data-ttu-id="65682-102">SQL Server Compact Edition 変換先</span><span class="sxs-lookup"><span data-stu-id="65682-102">SQL Server Compact Edition Destination</span></span>
  <span data-ttu-id="65682-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 変換先では、データが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact データベースに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="65682-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination writes data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact databases.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="65682-104">64 ビット コンピューターでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact データ ソースに接続するパッケージを 32 ビット モードで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65682-104">On a 64-bit computer, you must run packages that connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact data sources in 32-bit mode.</span></span> <span data-ttu-id="65682-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Compact データ ソースへの接続に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact Provider は、32 ビット版でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="65682-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact provider that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] uses to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact data sources is available only in a 32-bit version.</span></span>  
  
 <span data-ttu-id="65682-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 変換先を構成するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 変換先でデータが挿入されるテーブルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="65682-106">You configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination by specifying the name of the table into which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination inserts the data.</span></span> <span data-ttu-id="65682-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 変換先のカスタム プロパティ TableName には、テーブル名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="65682-107">The custom property TableName of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination contains the table name.</span></span>  
  
 <span data-ttu-id="65682-108">この変換先ではデータ ソースへの接続に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 接続マネージャーが使用され、この接続マネージャーによって、使用する OLE DB プロバイダーが指定されます。</span><span class="sxs-lookup"><span data-stu-id="65682-108">This destination uses an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connection manager to connect to a data source, and the connection manager specifies the OLE DB provider to use.</span></span> <span data-ttu-id="65682-109">詳細については、「 [SQL Server Compact Edition 接続マネージャー](../connection-manager/sql-server-compact-edition-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65682-109">For more information, see [SQL Server Compact Edition Connection Manager](../connection-manager/sql-server-compact-edition-connection-manager.md).</span></span>  
  
 <span data-ttu-id="65682-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 変換先には、パッケージの読み込み時にプロパティ式で更新できる、TableName カスタム プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="65682-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination includes the TableName custom property, which can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="65682-111">詳細については、「[Integration Services (SSIS) の式](../expressions/integration-services-ssis-expressions.md)」、「[パッケージでプロパティ式を使用する](../expressions/use-property-expressions-in-packages.md)」、および「[SQL Server Compact Edition 変換先のカスタム プロパティ](sql-server-compact-edition-destination-custom-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65682-111">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md), and [SQL Server Compact Edition Destination Custom Properties](sql-server-compact-edition-destination-custom-properties.md).</span></span>  
  
 <span data-ttu-id="65682-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 変換先の入力は 1 つで、エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="65682-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact destination has one input and does not support an error output.</span></span>  
  
## <a name="configuration-of-the-sql-server-compact-edition-destination"></a><span data-ttu-id="65682-113">SQL Server Compact Edition 変換先の構成</span><span class="sxs-lookup"><span data-stu-id="65682-113">Configuration of the SQL Server Compact Edition Destination</span></span>  
 <span data-ttu-id="65682-114">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="65682-114">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="65682-115">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="65682-115">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="65682-116">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="65682-116">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="65682-117">Common Properties</span><span class="sxs-lookup"><span data-stu-id="65682-117">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="65682-118">SQL Server 変換先のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="65682-118">SQL Server Destination Custom Properties</span></span>](sql-server-destination-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="65682-119">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="65682-119">Related Tasks</span></span>  
 <span data-ttu-id="65682-120">このコンポーネントのプロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65682-120">For more information about how to set properties of this component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65682-121">参照</span><span class="sxs-lookup"><span data-stu-id="65682-121">See Also</span></span>  
 [<span data-ttu-id="65682-122">データ フロー</span><span class="sxs-lookup"><span data-stu-id="65682-122">Data Flow</span></span>](data-flow.md)  
  
  
