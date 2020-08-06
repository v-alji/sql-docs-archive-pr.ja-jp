---
title: OLE DB コマンド変換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbcommandtrans.f1
helpviewer_keywords:
- statements [Integration Services]
- OLE DB Command transformation
ms.assetid: baa6735c-5acf-4759-b077-1216aca16c6c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a6b0498d0ae5fa61a00cc7f6fc89e4dc506cd25a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743429"
---
# <a name="ole-db-command-transformation"></a><span data-ttu-id="c278b-102">OLE DB コマンド変換</span><span class="sxs-lookup"><span data-stu-id="c278b-102">OLE DB Command Transformation</span></span>
  <span data-ttu-id="c278b-103">OLE DB コマンド変換は、データ フローの各行に対して SQL ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="c278b-103">The OLE DB Command transformation runs an SQL statement for each row in a data flow.</span></span> <span data-ttu-id="c278b-104">たとえば、データベース テーブル内に行を挿入したり、行を更新または削除する SQL ステートメントを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c278b-104">For example, you can run an SQL statement that inserts, updates, or deletes rows in a database table.</span></span>  
  
 <span data-ttu-id="c278b-105">OLE DB コマンド変換は、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="c278b-105">You can configure the OLE DB Command Transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="c278b-106">各行に対して変換が実行する SQL ステートメントを指定します。</span><span class="sxs-lookup"><span data-stu-id="c278b-106">Provide the SQL statement that the transformation runs for each row.</span></span>  
  
-   <span data-ttu-id="c278b-107">SQL ステートメントがタイムアウトになる時間を秒数で指定します。</span><span class="sxs-lookup"><span data-stu-id="c278b-107">Specify the number of seconds before the SQL statement times out.</span></span>  
  
-   <span data-ttu-id="c278b-108">既定のコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="c278b-108">Specify the default code page.</span></span>  
  
 <span data-ttu-id="c278b-109">通常、SQL ステートメントにはパラメーターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c278b-109">Typically, the SQL statement includes parameters.</span></span> <span data-ttu-id="c278b-110">パラメーター値は変換入力内の外部列に格納され、入力列を外部列にマップすることによって、入力列をパラメーターにマップします。</span><span class="sxs-lookup"><span data-stu-id="c278b-110">The parameter values are stored in external columns in the transformation input, and mapping an input column to an external column maps an input column to a parameter.</span></span> <span data-ttu-id="c278b-111">たとえば、 **ProductKey** 列の値を使用し、 **DimProduct** テーブルの行を探して削除するには、 **Param_0** という名前の外部列を **ProductKey** という名前の入力列にマップし、SQL ステートメント `DELETE FROM DimProduct WHERE ProductKey = ?`を実行します。</span><span class="sxs-lookup"><span data-stu-id="c278b-111">For example, to locate rows in the **DimProduct** table by the value in their **ProductKey** column and then delete them, you can map the external column named **Param_0** to the input column named **ProductKey,** and then run the SQL statement `DELETE FROM DimProduct WHERE ProductKey = ?`..</span></span> <span data-ttu-id="c278b-112">OLE DB コマンド変換で用意されているパラメーター名は変更できません。</span><span class="sxs-lookup"><span data-stu-id="c278b-112">The OLE DB Command transformation provides the parameter names and you cannot modify them.</span></span> <span data-ttu-id="c278b-113">パラメーター名は、 **Param_0**、 **Param_1**のように指定されます。</span><span class="sxs-lookup"><span data-stu-id="c278b-113">The parameter names are **Param_0**, **Param_1**, and so on.</span></span>  
  
 <span data-ttu-id="c278b-114">**[詳細エディター]** ダイアログ ボックスを使用して OLE DB コマンド変換を構成する場合、SQL ステートメント内のパラメーターは変換入力内の外部列に自動的にマップされ、 **[最新の情報に更新]** ボタンをクリックすると、各パラメーターの特性が定義されます。</span><span class="sxs-lookup"><span data-stu-id="c278b-114">If you configure the OLE DB Command transformation by using the **Advanced Editor** dialog box, the parameters in the SQL statement may be mapped automatically to external columns in the transformation input, and the characteristics of each parameter defined, by clicking the **Refresh** button.</span></span> <span data-ttu-id="c278b-115">ただし、OLE DB コマンド変換で使用する OLE DB プロバイダーが、パラメーターから取得するパラメーター情報をサポートしていない場合、外部列を手動で構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c278b-115">However, if the OLE DB provider that the OLE DB Command transformation uses does not support deriving parameter information from the parameter, you must configure the external columns manually.</span></span> <span data-ttu-id="c278b-116">つまり、外部入力に渡すパラメーターごとに列を変換に追加し、 **Param_0**などの名前が使用されるように列名を更新します。さらに、DBParamInfoFlags プロパティの値を指定し、パラメーター値を含む入力列を外部列にマップする操作が必要です。</span><span class="sxs-lookup"><span data-stu-id="c278b-116">This means that you must add a column for each parameter to the external input to the transformation, update the column names to use names like **Param_0**, specify the value of the DBParamInfoFlags property, and map the input columns that contain parameter values to the external columns.</span></span>  
  
 <span data-ttu-id="c278b-117">DBParamInfoFlags の値は、パラメーターの特性を表します。</span><span class="sxs-lookup"><span data-stu-id="c278b-117">The value of DBParamInfoFlags represents the characteristics of the parameter.</span></span> <span data-ttu-id="c278b-118">たとえば、値 **1** は、パラメーターが入力パラメーターであることを表し、値 **65** は、パラメーターが入力パラメーターであり、NULL 値を含めることができることを表します。</span><span class="sxs-lookup"><span data-stu-id="c278b-118">For example, the value **1** specifies that the parameter is an input parameter, and the value **65** specifies that the parameter is an input parameter and may contain a null value.</span></span> <span data-ttu-id="c278b-119">この値は、OLE DB DBPARAMFLAGSENUM 列挙値と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c278b-119">The values must match the values in the OLE DB DBPARAMFLAGSENUM enumeration.</span></span> <span data-ttu-id="c278b-120">詳細については、OLE DB のリファレンス マニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c278b-120">For more information, see the OLE DB reference documentation.</span></span>  
  
 <span data-ttu-id="c278b-121">OLE DB コマンド変換には、`SQLCommand` カスタム プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="c278b-121">The OLE DB Command transformation includes the `SQLCommand` custom property.</span></span> <span data-ttu-id="c278b-122">このプロパティは、パッケージの読み込み時にプロパティ式で更新できます。</span><span class="sxs-lookup"><span data-stu-id="c278b-122">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="c278b-123">詳細については、「[Integration Services &#40;SSIS&#41; の式](../../expressions/integration-services-ssis-expressions.md)」、「[パッケージでプロパティ式を使用する](../../expressions/use-property-expressions-in-packages.md)」、および「[変換のカスタム プロパティ](transformation-custom-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c278b-123">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="c278b-124">この変換は、1 つの入力、1 つの標準出力、および 1 つのエラー出力をとります。</span><span class="sxs-lookup"><span data-stu-id="c278b-124">This transformation has one input, one regular output, and one error output.</span></span>  
  
## <a name="logging"></a><span data-ttu-id="c278b-125">ログ記録</span><span class="sxs-lookup"><span data-stu-id="c278b-125">Logging</span></span>  
 <span data-ttu-id="c278b-126">OLE DB コマンド変換による外部データ プロバイダーの呼び出しをログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="c278b-126">You can log the calls that the OLE DB Command transformation makes to external data providers.</span></span> <span data-ttu-id="c278b-127">このログ機能を使用すると、OLE DB コマンド変換による外部データ ソースへの接続およびコマンドに関するトラブルシューティングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c278b-127">You can use this logging capability to troubleshoot the connections and commands to external data sources that the OLE DB Command transformation performs.</span></span> <span data-ttu-id="c278b-128">OLE DB コマンド変換による外部データ プロバイダーの呼び出しのログを記録するには、パッケージ ログ記録を有効にして、パッケージ レベルで **Diagnostic** イベントを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c278b-128">To log the calls that the OLE DB Command transformation makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="c278b-129">詳細については、「 [パッケージ実行のトラブルシューティング ツール](../../troubleshooting/troubleshooting-tools-for-package-execution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c278b-129">For more information, see [Troubleshooting Tools for Package Execution](../../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="c278b-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="c278b-130">Related Tasks</span></span>  
 <span data-ttu-id="c278b-131">変換は、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーまたはオブジェクト モデルを使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="c278b-131">You can configure the transformation by either using the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or the object model.</span></span> <span data-ttu-id="c278b-132">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーを使用して変換を構成する方法については、「  [OLE DB コマンド変換を構成する](../../configure-the-ole-db-command-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c278b-132">For details about configuring the transformation using the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] designer, see  [Configure the OLE DB Command Transformation](../../configure-the-ole-db-command-transformation.md).</span></span> <span data-ttu-id="c278b-133">プログラムによってこの変換を構成する方法の詳細については、開発者ガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c278b-133">See the Developer Guide for details about programmatically configuring this transformation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c278b-134">参照</span><span class="sxs-lookup"><span data-stu-id="c278b-134">See Also</span></span>  
 <span data-ttu-id="c278b-135">[データ フロー](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="c278b-135">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="c278b-136">Integration Services の変換</span><span class="sxs-lookup"><span data-stu-id="c278b-136">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
