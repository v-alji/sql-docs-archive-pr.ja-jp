---
title: トラブルシューティングツールのパッケージ接続 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services packages, troubleshooting
- SSIS packages, troubleshooting
- Integration Services, troubleshooting
- connectivity [Integration Services], troubleshooting
- errors [Integration Services], troubleshooting
- packages [Integration Services], troubleshooting
ms.assetid: 08a019f5-8ba7-4527-97c1-e9846d4022ff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1baac9af5a30fdc0f5b15e8ac56eb5badacc0edb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715554"
---
# <a name="troubleshooting-tools-package-connectivity"></a><span data-ttu-id="c9284-102">トラブルシューティング ツールのパッケージ接続</span><span class="sxs-lookup"><span data-stu-id="c9284-102">Troubleshooting Tools Package Connectivity</span></span>
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="c9284-103">には、パッケージと、パッケージがデータを抽出して読み込むデータ ソースとの接続のトラブルシューティングを行うための、機能とツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="c9284-103">includes features and tools that you can use to troubleshoot connectivity between packages and the data sources from which packages extract and load data.</span></span>  
  
## <a name="troubleshooting-issues-with-external-data-providers"></a><span data-ttu-id="c9284-104">外部データ プロバイダーの問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="c9284-104">Troubleshooting Issues with External Data Providers</span></span>  
 <span data-ttu-id="c9284-105">多くのパッケージが、外部データ プロバイダーとのやり取りで失敗します。</span><span class="sxs-lookup"><span data-stu-id="c9284-105">Many packages fail during interactions with external data providers.</span></span> <span data-ttu-id="c9284-106">ところが、これらのプロバイダーが [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に返すメッセージには、多くの場合、トラブルシューティングを開始するための十分な情報が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="c9284-106">However, the messages that those providers return to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] frequently do not provide enough information to start troubleshooting the interaction.</span></span> <span data-ttu-id="c9284-107">トラブルシューティングのニーズに対応するために、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、パッケージと外部データ ソースとのやり取りに関するトラブルシューティングに使用できる新しいログ メッセージが採用されています。</span><span class="sxs-lookup"><span data-stu-id="c9284-107">To address this troubleshooting need, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes logging messages that you can use to troubleshoot a package's interaction with external data sources.</span></span>  
  
-   <span data-ttu-id="c9284-108">**ログ記録を有効にして、パッケージの Diagnostic イベントを選択すると、トラブルシューティング メッセージが表示されます**。</span><span class="sxs-lookup"><span data-stu-id="c9284-108">**Enable logging and select the package's Diagnostic event to see the troubleshooting messages**.</span></span> <span data-ttu-id="c9284-109">次に示す [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] コンポーネントは、すべての外部データ プロバイダーの呼び出しの前後に、メッセージをログに出力できます。</span><span class="sxs-lookup"><span data-stu-id="c9284-109">The following [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components are capable of writing a message to the log before and after every call to an external data provider:</span></span>  
  
    -   <span data-ttu-id="c9284-110">OLE DB 接続マネージャー、OLE DB ソース、および OLE DB 変換先</span><span class="sxs-lookup"><span data-stu-id="c9284-110">OLE DB connection manager, OLE DB source, and OLE DB destination</span></span>  
  
    -   [!INCLUDE[vstecado](../../includes/vstecado-md.md)] <span data-ttu-id="c9284-111">接続マネージャーおよび ADO NET 変換元</span><span class="sxs-lookup"><span data-stu-id="c9284-111">connection manager and ADO NET source</span></span>  
  
    -   <span data-ttu-id="c9284-112">SQL 実行タスク</span><span class="sxs-lookup"><span data-stu-id="c9284-112">Execute SQL task</span></span>  
  
    -   <span data-ttu-id="c9284-113">参照変換、OLE DB コマンド変換、および緩やかに変化するディメンション変換</span><span class="sxs-lookup"><span data-stu-id="c9284-113">Lookup transformation, OLE DB Command transformation, and Slowly Changing Dimension transformation</span></span>  
  
     <span data-ttu-id="c9284-114">ログ メッセージには、呼び出されるメソッドの名前が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c9284-114">The log messages include the name of the method being called.</span></span> <span data-ttu-id="c9284-115">たとえば、これらのログ メッセージには OLE DB `Open` オブジェクトの `Connection` メソッド、または `ExecuteNonQuery` オブジェクトの `Command` メソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c9284-115">For example, these log messages might include the `Open` method of an OLE DB `Connection` object or the `ExecuteNonQuery` method of a `Command` object.</span></span> <span data-ttu-id="c9284-116">このメッセージの形式は次のとおりです。"%1!s!" は</span><span class="sxs-lookup"><span data-stu-id="c9284-116">The messages have the following format, where '%1!s!'</span></span> <span data-ttu-id="c9284-117">メソッド情報のプレースホルダーです。</span><span class="sxs-lookup"><span data-stu-id="c9284-117">is a placeholder for the method information:</span></span>  
  
    ```  
    ExternalRequest_pre: The object is ready to make the following external request: '%1!s!'.  
    ExternalRequest_post: '%1!s!'. The external request has completed.  
    ```  
  
     <span data-ttu-id="c9284-118">外部データ プロバイダーとのやり取りに関するトラブルシューティングを行うには、ログを表示して、"前の" メッセージ (`ExternalRequest_pre`) に対応する "後の" メッセージがあるかどうかを確認します (`ExternalRequest_post`)。</span><span class="sxs-lookup"><span data-stu-id="c9284-118">To troubleshoot the interaction with the external data provider, review the log to see whether every "before" message (`ExternalRequest_pre`) has a corresponding "after" message (`ExternalRequest_post`).</span></span> <span data-ttu-id="c9284-119">対応する "後の" メッセージがない場合は、外部データ プロバイダーが予測どおりに応答しなかったことになります。</span><span class="sxs-lookup"><span data-stu-id="c9284-119">If there is no corresponding "after" message, you know that the external data provider did not respond as expected.</span></span>  
  
     <span data-ttu-id="c9284-120">次の例では、これらのログ メッセージを含んでいるログの一部を示しています。</span><span class="sxs-lookup"><span data-stu-id="c9284-120">The following example shows some sample rows from a log that contains these logging messages:</span></span>  
  
    ```  
    ExternalRequest_pre: The object is ready to make the following external request: 'ITransactionJoin::JoinTransaction'.  
    ExternalRequest_post: 'ITransactionJoin::JoinTransaction succeeded'. The external request has completed.  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.Open'.  
    ExternalRequest_post: 'IDbConnection.Open succeeded'. The external request has completed.  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.CreateCommand'.  
    ExternalRequest_post: 'IDbConnection.CreateCommand finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbCommand.ExecuteReader'.  
    ExternalRequest_post: 'IDbCommand.ExecuteReader finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDataReader.GetSchemaTable'.  
    ExternalRequest_post: 'IDataReader.GetSchemaTable finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDataReader.Close'.  
    ExternalRequest_post: 'IDataReader.Close finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.Close'.  
    ExternalRequest_post: 'IDbConnection.Close finished'. The external request has completed."  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c9284-121">参照</span><span class="sxs-lookup"><span data-stu-id="c9284-121">See Also</span></span>  
 <span data-ttu-id="c9284-122">[パッケージ開発のトラブルシューティング ツール](troubleshooting-tools-for-package-development.md) </span><span class="sxs-lookup"><span data-stu-id="c9284-122">[Troubleshooting Tools for Package Development](troubleshooting-tools-for-package-development.md) </span></span>  
 [<span data-ttu-id="c9284-123">パッケージ実行のトラブルシューティング ツール</span><span class="sxs-lookup"><span data-stu-id="c9284-123">Troubleshooting Tools for Package Execution</span></span>](troubleshooting-tools-for-package-execution.md)  
  
  
