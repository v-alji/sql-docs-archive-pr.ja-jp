---
title: DataReader 変換先 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.datareaderdest.f1
helpviewer_keywords:
- DataReader destination
- destinations [Integration Services], DataReader
ms.assetid: 56fcc4bf-c901-42c3-a71d-110039293431
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 40cfe5d99c33eb19d415f204173005a64bde7855
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742462"
---
# <a name="datareader-destination"></a><span data-ttu-id="79d0e-102">DataReader 変換先</span><span class="sxs-lookup"><span data-stu-id="79d0e-102">DataReader Destination</span></span>
  <span data-ttu-id="79d0e-103">DataReader 変換先は、ADO.NET `DataReader` インターフェイスを使用して、データ フローのデータを公開します。</span><span class="sxs-lookup"><span data-stu-id="79d0e-103">The DataReader destination exposes the data in a data flow by using the ADO.NET `DataReader` interface.</span></span> <span data-ttu-id="79d0e-104">公開すると、そのデータを他のアプリケーションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="79d0e-104">The data can then be consumed by other applications.</span></span> <span data-ttu-id="79d0e-105">たとえば、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートのデータ ソースを構成して、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの実行結果を使用できます。</span><span class="sxs-lookup"><span data-stu-id="79d0e-105">For example, you can configure the data source of a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report to use the result of running a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="79d0e-106">構成するには、DataReader 変換先を実装するデータ フローを作成します。</span><span class="sxs-lookup"><span data-stu-id="79d0e-106">To do this, you create a data flow that implements the DataReader destination.</span></span>  
  
 <span data-ttu-id="79d0e-107">プログラムで DataReader 変換先にアクセスして値を読み取る方法の詳細については、「 [ローカル パッケージの出力の読み込み](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="79d0e-107">For information about accessing and reading values in the DataReader destination programmatically, see [Loading the Output of a Local Package](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md).</span></span>  
  
## <a name="configuration-of-the-datareader-destination"></a><span data-ttu-id="79d0e-108">DataReader 変換先の構成</span><span class="sxs-lookup"><span data-stu-id="79d0e-108">Configuration of the DataReader Destination</span></span>  
 <span data-ttu-id="79d0e-109">DataReader 変換先のタイムアウト値を指定して、タイムアウトが発生した場合に変換先が失敗になるようにするかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="79d0e-109">You can specify a time-out value for the DataReader destination and indicate whether the destination should fail if a time-out occurs.</span></span> <span data-ttu-id="79d0e-110">タイムアウトは、アプリケーションが指定した時間内にデータを要求しない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="79d0e-110">A time-out occurs if the application does not ask for data within the specified time.</span></span>  
  
 <span data-ttu-id="79d0e-111">DataReader 変換先は 1 つの入力をとります。</span><span class="sxs-lookup"><span data-stu-id="79d0e-111">The DataReader destination has one input.</span></span> <span data-ttu-id="79d0e-112">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="79d0e-112">It does not support an error output.</span></span>  
  
 <span data-ttu-id="79d0e-113">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="79d0e-113">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="79d0e-114">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="79d0e-114">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="79d0e-115">Common Properties</span><span class="sxs-lookup"><span data-stu-id="79d0e-115">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="79d0e-116">DataReader 変換先のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="79d0e-116">DataReader Destination Custom Properties</span></span>](datareader-destination-custom-properties.md)  
  
 <span data-ttu-id="79d0e-117">プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79d0e-117">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
