---
title: レコードセット変換先 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.recordsetdest.f1
helpviewer_keywords:
- Recordset destination
- ADO recordsets [Integration Services]
- destinations [Integration Services], Recordset
- in-memory ADO recordsets [Integration Services]
ms.assetid: be973cf1-c4ff-49f8-987e-314c08ef98e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c1acc29c904e9020721e8ac62dff09a8ec29a392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633914"
---
# <a name="recordset-destination"></a><span data-ttu-id="2c3f8-102">レコードセット変換先</span><span class="sxs-lookup"><span data-stu-id="2c3f8-102">Recordset Destination</span></span>
  <span data-ttu-id="2c3f8-103">レコードセット変換先は、インメモリ ADO レコードセットを作成して設定します。</span><span class="sxs-lookup"><span data-stu-id="2c3f8-103">The Recordset destination creates and populates an in-memory ADO recordset.</span></span> <span data-ttu-id="2c3f8-104">レコードセットの形態は、レコードセット変換先への入力によってデザイン時に定義されます。</span><span class="sxs-lookup"><span data-stu-id="2c3f8-104">The shape of the recordset is defined by the input to the Recordset destination at design time.</span></span>  
  
## <a name="configuration-of-the-recordset-destination"></a><span data-ttu-id="2c3f8-105">レコードセット変換先の構成</span><span class="sxs-lookup"><span data-stu-id="2c3f8-105">Configuration of the Recordset Destination</span></span>  
 <span data-ttu-id="2c3f8-106">レコードセット変換先を構成するには、ADO レコードセットを格納する変数を指定します。</span><span class="sxs-lookup"><span data-stu-id="2c3f8-106">You configure the Recordset destination by specifying the variable that stores the ADO recordset.</span></span>  
  
 <span data-ttu-id="2c3f8-107">実行時に、ADO レコードセットは、レコードセット変換先の VariableName プロパティで指定されたオブジェクト型の変数に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="2c3f8-107">At run time, an ADO recordset is written to the variable of type, Object, that is specified in the VariableName property of the Recordset destination.</span></span> <span data-ttu-id="2c3f8-108">その後、この変数はスクリプトおよび他のパッケージ要素で使用できるため、レコードセットはデータ フローの外部で利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="2c3f8-108">The variable then makes the Recordset available outside the data flow, where it can be used by scripts and other package elements.</span></span>  
  
 <span data-ttu-id="2c3f8-109">この変換先は 1 つの入力をとります。</span><span class="sxs-lookup"><span data-stu-id="2c3f8-109">This source has one input.</span></span> <span data-ttu-id="2c3f8-110">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2c3f8-110">It does not support an error output.</span></span>  
  
 <span data-ttu-id="2c3f8-111">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="2c3f8-111">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="2c3f8-112">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="2c3f8-112">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="2c3f8-113">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c3f8-113">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="2c3f8-114">Common Properties</span><span class="sxs-lookup"><span data-stu-id="2c3f8-114">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="2c3f8-115">レコードセット変換先のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="2c3f8-115">Recordset Destination Custom Properties</span></span>](recordset-destination-custom-properties.md)  
  
 <span data-ttu-id="2c3f8-116">データ フロー コンポーネントのプロパティの設定方法については、「 [データ フロー コンポーネントのプロパティを設定する](set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c3f8-116">For more information about how to set the properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="2c3f8-117">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="2c3f8-117">Related Tasks</span></span>  
 [<span data-ttu-id="2c3f8-118">レコードセット変換先を使用する</span><span class="sxs-lookup"><span data-stu-id="2c3f8-118">Use a Recordset Destination</span></span>](recordset-destination.md)  
  
  
