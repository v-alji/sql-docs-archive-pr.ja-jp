---
title: ssbdiagnose ユーティリティ (Service Broker) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- Service Broker, runtime reports
- Service Broker, command prompt utilities
- troubleshooting [Service Broker], conversations
- troubleshooting [Service Broker], configurations
- command prompt utilities [Service Broker]
- Service Broker, troubleshooting
- Service Broker, configuration reports
- Service Broker, tools
- troubleshooting [Service Broker], runtime
- conversations [Service Broker], troubleshooting
- troubleshooting [Service Broker], ssbdiagnose utility
- tools [Service Broker], ssbdiagnose
- Service Broker, ssbdiagnose utility
- ssbdiagnose
ms.assetid: 0c1636e8-a3db-438e-be4c-1ea40d1f4877
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8efc581eebd7d8fa7fa265abb54168af78b57ca2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720607"
---
# <a name="ssbdiagnose-utility-service-broker"></a><span data-ttu-id="eca5d-102">ssbdiagnose ユーティリティ (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="eca5d-102">ssbdiagnose Utility (Service Broker)</span></span>
  <span data-ttu-id="eca5d-103">**ssbdiagnose** ユーティリティは、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] メッセージ交換または [!INCLUDE[ssSB](../../includes/sssb-md.md)] サービスの構成に関する問題を報告します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-103">The **ssbdiagnose** utility reports issues in [!INCLUDE[ssSB](../../includes/sssb-md.md)] conversations or the configuration of [!INCLUDE[ssSB](../../includes/sssb-md.md)] services.</span></span> <span data-ttu-id="eca5d-104">構成チェックは 2 つまたは 1 つのサービスに対して実行できます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-104">Configuration checks can be made for either two services or a single service.</span></span> <span data-ttu-id="eca5d-105">問題点は、コマンド プロンプト ウィンドウにユーザーが解釈できる形式で報告されるか、ファイルまたは別のプログラムにリダイレクトできる XML 形式で報告されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-105">Issues are reported either in the command prompt window as human-readable text, or as formatted XML that can be redirected to a file or another program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eca5d-106">構文</span><span class="sxs-lookup"><span data-stu-id="eca5d-106">Syntax</span></span>  
  
```  
  
      ssbdiagnose   
[ [ -XML ]  
    [ -LEVEL { ERROR | WARNING | INFO } ]  
  [-IGNOREerror_id ] [ ...n]  
    [ <baseconnectionoptions> ]  
  { <configurationreport> | <runtimereport> }  
]  
| -?  
  
<configurationreport> ::=  
    CONFIGURATION  
  { [ FROM SERVICEservice_name  
      [ <fromconnectionoptions> ]  
      [ MIRROR <mirrorconnectionoptions> ]  
    ]  
    [ TO SERVICEservice_name[, broker_id ]  
      [ <toconnectionoptions> ]  
      [ MIRROR <mirrorconnectionoptions> ]  
    ]  
  }  
    ON CONTRACTcontract_name  
  [ ENCRYPTION { ON | OFF | ANONYMOUS } ]  
  
<runtime_report> ::=  
    RUNTIME  
    [-SHOWEVENTS ]  
        [ -NEW  
         [ -ID { conversation_handle  
                | conversation_group_id  
                 | conversation_id  
                  }  
        ] [ ...n]  
        ]  
    [ -TIMEOUTtimeout_interval ]  
    [ <runtimeconnectionoptions> ]  
  
<baseconnectionoptions> ::=  
  <connectionoptions>  
  
<fromconnectionoptions> ::=  
  <connectionoptions>  
  
<toconnectionoptions> ::=  
  <connectionoptions>  
  
<mirrorconnectionoptions> ::=  
  <connectionoptions>  
  
<runtimeconnectionoptions> ::=  
  [ CONNECT TO <connectionoptions> ] [ ...n]  
  
<connectionoptions> ::=  
    [ -E | { -Ulogin_id [ -Ppassword ] } ]  
  [ -Sserver_name[\instance_name] ]  
  [ -ddatabase_name ]  
  [ -llogin_timeout ]  
  
```  
  
## <a name="command-line-options"></a><span data-ttu-id="eca5d-107">コマンド ライン オプション</span><span class="sxs-lookup"><span data-stu-id="eca5d-107">Command Line Options</span></span>  
 <span data-ttu-id="eca5d-108">**-XML**</span><span class="sxs-lookup"><span data-stu-id="eca5d-108">**-XML**</span></span>  
 <span data-ttu-id="eca5d-109">**ssbdiagnose** の出力を XML 形式で生成することを指定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-109">Specifies that the **ssbdiagnose** output be generated as formatted XML.</span></span> <span data-ttu-id="eca5d-110">この出力は、ファイルまたは他のアプリケーションにリダイレクトできます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-110">This can be redirected to a file or to another application.</span></span> <span data-ttu-id="eca5d-111">**-XML** が指定されていない場合は、 **ssbdiagnose** の出力がユーザーが解釈できる形式に設定されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-111">If **-XML** is not specified, the **ssbdiagnose** output is formatted as human-readable text.</span></span>  
  
 <span data-ttu-id="eca5d-112">**-LEVEL** { **ERROR** | **WARNING** | **INFO**}</span><span class="sxs-lookup"><span data-stu-id="eca5d-112">**-LEVEL** { **ERROR** | **WARNING** | **INFO**}</span></span>  
 <span data-ttu-id="eca5d-113">報告するメッセージのレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-113">Specifies the level of messages to report.</span></span>  
  
 <span data-ttu-id="eca5d-114">**ERROR**: エラー メッセージのみを報告します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-114">**ERROR**: report only error messages.</span></span>  
  
 <span data-ttu-id="eca5d-115">**WARNING**: エラー メッセージと警告メッセージを報告します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-115">**WARNING**: report error and warning messages.</span></span>  
  
 <span data-ttu-id="eca5d-116">**INFO**: エラー メッセージ、警告メッセージ、および情報メッセージを報告します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-116">**INFO**: report error, warning, and informational messages.</span></span>  
  
 <span data-ttu-id="eca5d-117">既定の設定は **WARNING**です。</span><span class="sxs-lookup"><span data-stu-id="eca5d-117">The default setting is **WARNING**.</span></span>  
  
 <span data-ttu-id="eca5d-118">**-IGNORE** *error_id*</span><span class="sxs-lookup"><span data-stu-id="eca5d-118">**-IGNORE** *error_id*</span></span>  
 <span data-ttu-id="eca5d-119">指定した *error_id* のエラーまたはメッセージがレポートから除外されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-119">Specifies that errors or messages that have the specified *error_id* not be included in reports.</span></span> <span data-ttu-id="eca5d-120">**-IGNORE** を複数回指定すると、複数のメッセージ ID を除外することができます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-120">You can specify **-IGNORE** multiple times to suppress multiple message IDs.</span></span>  
  
 **\<baseconnectionoptions>**  
 <span data-ttu-id="eca5d-121">接続オプションが特定の句に含まれていない場合に **ssbdiagnose** が使用する、基本的な接続情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-121">Specifies the base connection information that is used by **ssbdiagnose** when connection options are not included in a specific clause.</span></span> <span data-ttu-id="eca5d-122">特定の句で指定された接続情報は、**baseconnectionoption** の情報をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="eca5d-122">The connection information that is given in a specific clause overrides the **baseconnectionoption** information.</span></span> <span data-ttu-id="eca5d-123">優先的に使用される接続情報は、パラメーターごとに判別されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-123">This is performed separately for each parameter.</span></span> <span data-ttu-id="eca5d-124">たとえば、 **-S** と **-d** の両方が **baseconnetionoptions**で指定され、 **-d** のみが **toconnetionoptions**で指定されている場合、 **ssbdiagnose** では、 **baseconnetionoptions** の -S と **toconnetionoptions**の -d が使用されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-124">For example, if both **-S** and **-d** are specified in **baseconnetionoptions**, and only **-d** is specified in **toconnetionoptions**, **ssbdiagnose** uses -S from **baseconnetionoptions** and -d from **toconnetionoptions**.</span></span>  
  
 <span data-ttu-id="eca5d-125">**CONFIGURATION**</span><span class="sxs-lookup"><span data-stu-id="eca5d-125">**CONFIGURATION**</span></span>  
 <span data-ttu-id="eca5d-126">[!INCLUDE[ssSB](../../includes/sssb-md.md)] サービスのペアまたは 1 つのサービスでの構成エラーのレポートを要求します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-126">Requests a report of configuration errors between a pair of [!INCLUDE[ssSB](../../includes/sssb-md.md)] services, or for a single service.</span></span>  
  
 <span data-ttu-id="eca5d-127">**FROM SERVICE** *service_name*</span><span class="sxs-lookup"><span data-stu-id="eca5d-127">**FROM SERVICE** *service_name*</span></span>  
 <span data-ttu-id="eca5d-128">メッセージ交換を開始するサービスを指定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-128">Specifies the service that initiates conversations.</span></span>  
  
 **\<fromconnectionoptions>**  
 <span data-ttu-id="eca5d-129">発信側サービスが格納されているデータベースへの接続に必要な情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-129">Specifies the information that is required to connect to the database that holds the initiator service.</span></span> <span data-ttu-id="eca5d-130">**fromconnectionoptions** が指定されていない場合、 **ssbdiagnose** では **baseconnectionoptions** の接続情報を使用して発信側データベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-130">If **fromconnectionoptions** is not specified, **ssbdiagnose** uses the connection information from **baseconnectionoptions** to connect to the initiator database.</span></span> <span data-ttu-id="eca5d-131">**fromconnectionoptions** が指定されている場合は、発信側サービスが格納されているデータベースを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="eca5d-131">If **fromconnectionoptions** is specified it must include the database that contains the initiator service.</span></span> <span data-ttu-id="eca5d-132">**fromconnectionoptions** が指定されていない場合は、 **baseconnectionoptions** で発信側データベースを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eca5d-132">If **fromconnectionoptions** is not specified, the **baseconnectionoptions** must specify the initiator database.</span></span>  
  
 <span data-ttu-id="eca5d-133">**TO SERVICE** *service_name*[, *broker_id* ]</span><span class="sxs-lookup"><span data-stu-id="eca5d-133">**TO SERVICE** *service_name*[, *broker_id* ]</span></span>  
 <span data-ttu-id="eca5d-134">メッセージ交換の発信先サービスを指定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-134">Specifies the service that is the target for the conversations.</span></span>  
  
 <span data-ttu-id="eca5d-135">*service_name*: 発信先サービスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-135">*service_name*: specifies the name of the target service.</span></span>  
  
 <span data-ttu-id="eca5d-136">*broker_id*: 発信先データベースを示す [!INCLUDE[ssSB](../../includes/sssb-md.md)] ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-136">*broker_id*: specifies the [!INCLUDE[ssSB](../../includes/sssb-md.md)] ID that identifies the target database.</span></span> <span data-ttu-id="eca5d-137">*broker_id* は GUID です。</span><span class="sxs-lookup"><span data-stu-id="eca5d-137">*broker_id* is a GUID.</span></span> <span data-ttu-id="eca5d-138">発信先データベースで次のクエリを実行すると、この ID を検索できます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-138">You can run the following query in the target database to find it:</span></span>  
  
```  
SELECT service_broker_guid  
FROM sys.databases  
WHERE database_id = DB_ID();  
```  
  
 **\<toconnectionoptions>**  
 <span data-ttu-id="eca5d-139">発信先サービスが格納されているデータベースへの接続に必要な情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-139">Specifies the information that is required to connect the database that holds the target service.</span></span> <span data-ttu-id="eca5d-140">**toconnectionoptions** が指定されていない場合、 **ssbdiagnose** では **baseconnectionoptions** の接続情報を使用して発信先データベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-140">If **toconnectionoptions** is not specified, **ssbdiagnose** uses the connection information from **baseconnectionoptions** to connect to the target database.</span></span>  
  
 <span data-ttu-id="eca5d-141">**MIRROR**</span><span class="sxs-lookup"><span data-stu-id="eca5d-141">**MIRROR**</span></span>  
 <span data-ttu-id="eca5d-142">関連する [!INCLUDE[ssSB](../../includes/sssb-md.md)] サービスが、ミラー化されたデータベースでホストされます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-142">Specifies that the associated [!INCLUDE[ssSB](../../includes/sssb-md.md)] service is hosted in a mirrored database.</span></span> <span data-ttu-id="eca5d-143">**ssbdiagnose** は、サービスへのルートがミラー化されたルートであることを確認します。この場合、MIRROR_ADDRESS が CREATE ROUTE で指定されています。</span><span class="sxs-lookup"><span data-stu-id="eca5d-143">**ssbdiagnose** verifies that the route to the service is a mirrored route, where MIRROR_ADDRESS was specified on CREATE ROUTE.</span></span>  
  
 **\<mirrorconnectionoptions>**  
 <span data-ttu-id="eca5d-144">ミラー データベースへの接続に必要な情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-144">Specifies the information that is required to connect to the mirror database.</span></span> <span data-ttu-id="eca5d-145">**mirrorconnectionoptions** が指定されていない場合、 **ssbdiagnose** では **baseconnectionoptions** の接続情報を使用してミラー データベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-145">If **mirrorconnectionoptions** is not specified, **ssbdiagnose** uses the connection information from **baseconnectionoptions** to connect to the mirror database.</span></span>  
  
 <span data-ttu-id="eca5d-146">**ON CONTRACT** *contract_name*</span><span class="sxs-lookup"><span data-stu-id="eca5d-146">**ON CONTRACT** *contract_name*</span></span>  
 <span data-ttu-id="eca5d-147">指定されたコントラクトを使用する構成のみを **ssbdiagnose** でチェックするように要求します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-147">Requests that **ssbdiagnose** only check configurations that use the specified contract.</span></span> <span data-ttu-id="eca5d-148">ON CONTRACT が指定されていない場合、 **ssbdiagnose** では、DEFAULT という名前のコントラクトに関するレポートが生成されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-148">If ON CONTRACT is not specified, **ssbdiagnose** reports on the contract named DEFAULT.</span></span>  
  
 <span data-ttu-id="eca5d-149">**ENCRYPTION** { **ON** | **OFF** | **ANONYMOUS** }</span><span class="sxs-lookup"><span data-stu-id="eca5d-149">**ENCRYPTION** { **ON** | **OFF** | **ANONYMOUS** }</span></span>  
 <span data-ttu-id="eca5d-150">指定されたレベルの暗号化向けにダイアログが正しく構成されているかどうかを検証するように要求します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-150">Requests verification that the dialog is correctly configured for the specified level of encryption:</span></span>  
  
 <span data-ttu-id="eca5d-151">**ON**:既定の設定</span><span class="sxs-lookup"><span data-stu-id="eca5d-151">**ON**: Default setting.</span></span> <span data-ttu-id="eca5d-152">完全ダイアログ セキュリティが構成されているかどうかを検証します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-152">Full dialog security is configured.</span></span> <span data-ttu-id="eca5d-153">証明書がダイアログの両側に配置されていること、リモート サービス バインドが存在すること、および発信先サービスに対する GRANT SEND ステートメントで発信側ユーザーを指定していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-153">Certificates have been deployed on both sides of the dialog, a remote service binding is present, and the GRANT SEND statement for the target service specified the initiator user.</span></span>  
  
 <span data-ttu-id="eca5d-154">**OFF**:ダイアログ セキュリティが構成されていないかどうかを検証します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-154">**OFF**: No dialog security is configured.</span></span> <span data-ttu-id="eca5d-155">証明書が配置されていないこと、リモート サービス バインドが作成されていないこと、および発信側サービスに対する GRANT SEND ステートメントで **public** ロールを指定していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-155">No certificates have been deployed, no remote service binding was created, and the GRANT SEND for the initiator service specified the **public** role.</span></span>  
  
 <span data-ttu-id="eca5d-156">**ANONYMOUS**:匿名ダイアログ セキュリティが構成されているかどうかを検証します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-156">**ANONYMOUS**: Anonymous dialog security is configured.</span></span> <span data-ttu-id="eca5d-157">一方の証明書が配置されていること、リモート サービス バインドで匿名句が指定されていること、および発信先サービスに対する GRANT SEND ステートメントで **public** ロールを指定していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-157">One certificate has been deployed, the remote service binding specified the anonymous clause, and the GRANT SEND for the target service specified the **public** role.</span></span>  
  
 <span data-ttu-id="eca5d-158">**RUNTIME**</span><span class="sxs-lookup"><span data-stu-id="eca5d-158">**RUNTIME**</span></span>  
 <span data-ttu-id="eca5d-159">[!INCLUDE[ssSB](../../includes/sssb-md.md)] メッセージ交換の実行時エラーの原因である問題に関するレポートを要求します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-159">Requests a report of issues that cause runtime errors for a [!INCLUDE[ssSB](../../includes/sssb-md.md)] conversation.</span></span> <span data-ttu-id="eca5d-160">**-NEW** も **-ID** も指定されていない場合、 **ssbdiagnose** では、接続オプションで指定されたすべてのデータベース内のメッセージ交換をすべて監視します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-160">If neither **-NEW** or **-ID** are specified, **ssbdiagnose** monitors all conversations in all databases specified in the connection options.</span></span> <span data-ttu-id="eca5d-161">**-NEW** または **-ID** が指定されている場合、 **ssbdiagnose** では、パラメーターで指定された ID の一覧が作成されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-161">If **-NEW** or **-ID** are specified, **ssbdiagnose** builds a list of the IDs specified in the parameters.</span></span>  
  
 <span data-ttu-id="eca5d-162">**ssbdiagnose[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] は、実行中に、実行時エラーを示す**  イベントをすべて記録します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-162">While **ssbdiagnose** is running, it records all [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] events that indicate runtime errors.</span></span> <span data-ttu-id="eca5d-163">また、指定された ID に対して発生するイベントに加え、システムレベルのイベントも記録します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-163">It records the events that occur for the specified IDs, plus system-level events.</span></span> <span data-ttu-id="eca5d-164">実行時エラーが検出されると、 **ssbdiagnose** では、関連付けられている構成に対して構成レポートを実行します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-164">If runtime errors are encountered, **ssbdiagnose** runs a configuration report on the associated configuration.</span></span>  
  
 <span data-ttu-id="eca5d-165">既定では、出力レポートに実行時エラーは含まれず、構成の分析結果のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-165">By default, runtime errors are not included in the output report, only the results of the configuration analysis.</span></span> <span data-ttu-id="eca5d-166">レポートに実行時エラーを含めるには、 **-SHOWEVENTS** を使用してください。</span><span class="sxs-lookup"><span data-stu-id="eca5d-166">Use **-SHOWEVENTS** to have the runtime errors included in the report.</span></span>  
  
 <span data-ttu-id="eca5d-167">**-SHOWEVENTS**</span><span class="sxs-lookup"><span data-stu-id="eca5d-167">**-SHOWEVENTS**</span></span>  
 <span data-ttu-id="eca5d-168">**ssbdiagnose** で RUNTIME レポートの実行中に [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] イベントを報告するように指定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-168">Specifies that **ssbdiagnose** report [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] events during a RUNTIME report.</span></span> <span data-ttu-id="eca5d-169">エラー状態と見なされるイベントのみが報告されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-169">Only events that are considered error conditions are reported.</span></span> <span data-ttu-id="eca5d-170">既定では、 **ssbdiagnose** はエラー イベントを監視するだけで、エラー イベントをレポートに出力しません。</span><span class="sxs-lookup"><span data-stu-id="eca5d-170">By default, **ssbdiagnose** only monitors error events; it does not report them in the output.</span></span>  
  
 <span data-ttu-id="eca5d-171">**-NEW**</span><span class="sxs-lookup"><span data-stu-id="eca5d-171">**-NEW**</span></span>  
 <span data-ttu-id="eca5d-172">**ssbdiagnose** が実行を開始した後に開始される最初のメッセージ交換を、実行時に監視するように要求します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-172">Requests runtime monitoring of the first conversation that begins after **ssbdiagnose** starts running.</span></span>  
  
 <span data-ttu-id="eca5d-173">**-ID**</span><span class="sxs-lookup"><span data-stu-id="eca5d-173">**-ID**</span></span>  
 <span data-ttu-id="eca5d-174">指定されたメッセージ交換要素を実行時に監視するように要求します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-174">Requests runtime monitoring of the specified conversation elements.</span></span> <span data-ttu-id="eca5d-175">**-ID** は複数回指定できます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-175">You can specify **-ID** multiple times.</span></span>  
  
 <span data-ttu-id="eca5d-176">メッセージ交換ハンドルを指定すると、関連するメッセージ交換のエンドポイントに関連付けられたイベントのみが報告されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-176">If you specify a conversation handle, only events associated with the associated conversation endpoint are reported.</span></span> <span data-ttu-id="eca5d-177">メッセージ交換 ID を指定すると、そのメッセージ交換のすべてのイベントと、そのメッセージ交換の発信側と発信先のエンドポイントが報告されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-177">If you specify a conversation ID, all events for that conversation and its initiator and target endpoints are reported.</span></span> <span data-ttu-id="eca5d-178">メッセージ交換グループ ID が指定されている場合は、すべてのメッセージ交換のイベントと、メッセージ交換グループ内のエンドポイントが報告されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-178">If a conversation group ID is specified, all events for all conversations and endpoints in the conversation group are reported.</span></span>  
  
 <span data-ttu-id="eca5d-179">*conversation_handle*</span><span class="sxs-lookup"><span data-stu-id="eca5d-179">*conversation_handle*</span></span>  
 <span data-ttu-id="eca5d-180">アプリケーション内のメッセージ交換エンドポイントを識別する一意識別子です。</span><span class="sxs-lookup"><span data-stu-id="eca5d-180">A unique identifier that identifies a conversation endpoint in an application.</span></span> <span data-ttu-id="eca5d-181">メッセージ交換ハンドルは、メッセージ交換の一方のエンドポイントに対して一意であり、発信側と発信先のエンドポイントのメッセージ交換ハンドルは異なります。</span><span class="sxs-lookup"><span data-stu-id="eca5d-181">Conversation handles are unique to one endpoint of a conversation, the initiator and target endpoints have separate conversation handles.</span></span>  
  
 <span data-ttu-id="eca5d-182">メッセージ交換ハンドルは、 *@dialog_handle* **BEGIN DIALOG**ステートメントのパラメーターと、 `conversation_handle` **RECEIVE**ステートメントの結果セットの列によって、アプリケーションに返されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-182">Conversation handles are returned to applications by the *@dialog_handle* parameter of the **BEGIN DIALOG** statement, and the `conversation_handle` column in the result set of a **RECEIVE** statement.</span></span>  
  
 <span data-ttu-id="eca5d-183">メッセージ交換ハンドルは `conversation_handle` 、 **transmission_queue**および**conversation_endpoints**カタログビューの列で報告されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-183">Conversation handles are reported in the `conversation_handle` column of the **sys.transmission_queue** and **sys.conversation_endpoints** catalog views.</span></span>  
  
 <span data-ttu-id="eca5d-184">*conversation_group_id*</span><span class="sxs-lookup"><span data-stu-id="eca5d-184">*conversation_group_id*</span></span>  
 <span data-ttu-id="eca5d-185">メッセージ交換グループを識別する一意識別子です。</span><span class="sxs-lookup"><span data-stu-id="eca5d-185">The unique identifier that identifies a conversation group.</span></span>  
  
 <span data-ttu-id="eca5d-186">メッセージ交換グループ Id は *@conversation_group_id* 、 **GET メッセージ交換グループ**ステートメントのパラメーターと、 `conversation_group_id` **RECEIVE**ステートメントの結果セットの列によって、アプリケーションに返されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-186">Conversation group IDs are returned to applications by the *@conversation_group_id* parameter of the **GET CONVERSATION GROUP** statement and the `conversation_group_id` column in the result set of a **RECEIVE** statement.</span></span>  
  
 <span data-ttu-id="eca5d-187">メッセージ交換グループ Id は、 `conversation_group_id` **conversation_groups**および**conversation_endpoints**カタログビューの列で報告されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-187">Conversation group IDs are reported in the `conversation_group_id` columns of the **sys.conversation_groups** and **sys.conversation_endpoints** catalog views.</span></span>  
  
 <span data-ttu-id="eca5d-188">*conversation_id*</span><span class="sxs-lookup"><span data-stu-id="eca5d-188">*conversation_id*</span></span>  
 <span data-ttu-id="eca5d-189">メッセージ交換を識別する一意識別子です。</span><span class="sxs-lookup"><span data-stu-id="eca5d-189">The unique identifier that identifies a conversation.</span></span> <span data-ttu-id="eca5d-190">メッセージ交換 ID は、メッセージ交換の発信側と発信先の両方のエンドポイントで同じです。</span><span class="sxs-lookup"><span data-stu-id="eca5d-190">Conversation IDs are the same for both the initiator and target endpoints of a conversation.</span></span>  
  
 <span data-ttu-id="eca5d-191">メッセージ交換 Id は `conversation_id` 、 **conversation_endpoints**カタログビューの列で報告されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-191">Conversation IDs are reported in the `conversation_id` column of the **sys.conversation_endpoints** catalog view.</span></span>  
  
 <span data-ttu-id="eca5d-192">**-TIMEOUT** *timeout_interval*</span><span class="sxs-lookup"><span data-stu-id="eca5d-192">**-TIMEOUT** *timeout_interval*</span></span>  
 <span data-ttu-id="eca5d-193">**RUNTIME** レポートを実行する秒数を指定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-193">Specifies the number of seconds for a **RUNTIME** report to run.</span></span> <span data-ttu-id="eca5d-194">**-TIMEOUT** が指定されていない場合、ランタイム レポートは無制限に実行されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-194">If **-TIMEOUT** is not specified the runtime report runs indefinitely.</span></span> <span data-ttu-id="eca5d-195">**-TIMEOUT** は、**CONFIGURATION** レポートではなく、**RUNTIME** レポートのみで使用されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-195">**-TIMEOUT** is used only on **RUNTIME** reports, not **CONFIGURATION** reports.</span></span> <span data-ttu-id="eca5d-196">**-TIMEOUT** が指定されていない場合に **ssbdiagnose** を終了したり、タイムアウト間隔を経過する前にランタイム レポートを終了したりするには、Ctrl キーを押しながら C キーを押します。 **-**</span><span class="sxs-lookup"><span data-stu-id="eca5d-196">Use ctrl + C to quit **ssbdiagnose** if **-TIMEOUT** was not specified or to end a runtime report before the time**-** out interval expires.</span></span> <span data-ttu-id="eca5d-197">*timeout_interval* は 1 から 2,147,483,647 までの数値にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eca5d-197">*timeout_interval* must be a number between 1 and 2,147,483,647.</span></span>  
  
 **\<runtimeconnectionoptions>**  
 <span data-ttu-id="eca5d-198">監視対象のメッセージ交換要素に関連付けられたサービスが格納されているデータベースについての接続情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-198">Specifies the connection information for the databases that contain the services associated with conversation elements being monitored.</span></span> <span data-ttu-id="eca5d-199">すべてのサービスが同じデータベースに格納されている場合は、 **CONNECT TO** 句を 1 つ指定するだけで十分です。</span><span class="sxs-lookup"><span data-stu-id="eca5d-199">If all the services are in the same database, you only have to specify one **CONNECT TO** clause.</span></span> <span data-ttu-id="eca5d-200">サービスが異なるデータベースに格納されている場合は、各データベースに対して **CONNECT TO** 句を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eca5d-200">If the services are in separate databases you must supply a **CONNECT TO** clause for each database.</span></span> <span data-ttu-id="eca5d-201">**runtimeconnectionoptions** が指定されていない場合、 **ssbdiagnose** では **baseconnectionoptions**の接続情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-201">If **runtimeconnectionoptions** is not specified, **ssbdiagnose** uses the connection information from **baseconnectionoptions**.</span></span>  
  
 <span data-ttu-id="eca5d-202">**-E**</span><span class="sxs-lookup"><span data-stu-id="eca5d-202">**-E**</span></span>  
 <span data-ttu-id="eca5d-203">現在の Windows アカウントをログイン ID として使用して、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに対して Windows 認証接続を開きます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-203">Open a Windows Authentication connection to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by using your current Windows account as the login ID.</span></span> <span data-ttu-id="eca5d-204">ログインは **sysadmin** 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="eca5d-204">The login must be a member of the **sysadmin** fixed-server role.</span></span>  
  
 <span data-ttu-id="eca5d-205">-E オプションを使用すると、SQLCMDUSER 環境変数および SQLCMDPASSWORD 環境変数のユーザー設定とパスワード設定が無視されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-205">The -E option ignores the user and password settings of the SQLCMDUSER and SQLCMDPASSWORD environment variables.</span></span>  
  
 <span data-ttu-id="eca5d-206">**-E** も **ｰU** も指定されていない場合、 **ssbdiagnose** では、SQLCMDUSER 環境変数の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-206">If neither **-E** nor **-U** is specified, **ssbdiagnose** uses the value from the SQLCMDUSER environment variable.</span></span> <span data-ttu-id="eca5d-207">SQLCMDUSER も設定されていない場合、 **ssbdiagnose** では Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-207">If SQLCMDUSER is not set either, **ssbdiagnose** uses Windows Authentication.</span></span>  
  
 <span data-ttu-id="eca5d-208">**-E** オプションが **-U** オプションまたは **-P** オプションと共に使用されると、エラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-208">If the **-E** option is used together with the **-U** option or the **-P** option, an error message is generated.</span></span>  
  
 <span data-ttu-id="eca5d-209">**-U** *login_id*</span><span class="sxs-lookup"><span data-stu-id="eca5d-209">**-U** *login_id*</span></span>  
 <span data-ttu-id="eca5d-210">指定されたログイン ID を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証接続を開きます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-210">Open a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication connection by using the specified login ID.</span></span> <span data-ttu-id="eca5d-211">ログインは **sysadmin** 固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="eca5d-211">The login must be a member of the **sysadmin** fixed-server role.</span></span>  
  
 <span data-ttu-id="eca5d-212">**-E** も **ｰU** も指定されていない場合、 **ssbdiagnose** では、SQLCMDUSER 環境変数の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-212">If neither **-E** nor **-U** is specified, **ssbdiagnose** uses the value from the SQLCMDUSER environment variable.</span></span> <span data-ttu-id="eca5d-213">SQLCMDUSER も設定されていない場合、 **ssbdiagnose** では、 **ssbdiagnose**を実行しているユーザーの Windows アカウントに基づいた Windows 認証モードを使用して接続を試行します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-213">If SQLCMDUSER is not set either, **ssbdiagnose** tries to connect by using Windows Authentication mode based on the Windows account of the user who is running **ssbdiagnose**.</span></span>  
  
 <span data-ttu-id="eca5d-214">**-U** オプションを **-E** オプションと共に使用すると、エラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-214">If the **-U** option is used together with the **-E** option, an error message is generated.</span></span> <span data-ttu-id="eca5d-215">**-U** オプションの後に複数の引数があると、エラー メッセージが生成され、プログラムが終了します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-215">If the **-U** option is followed by more than one argument, an error message is generated and the program exits.</span></span>  
  
 <span data-ttu-id="eca5d-216">**-P** *password*</span><span class="sxs-lookup"><span data-stu-id="eca5d-216">**-P** *password*</span></span>  
 <span data-ttu-id="eca5d-217">**-U** ログイン ID のパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-217">Specifies the password for the **-U** login ID.</span></span> <span data-ttu-id="eca5d-218">パスワードでは大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-218">Passwords are case sensitive.</span></span> <span data-ttu-id="eca5d-219">**-U** オプションが使用され、 **-P** オプションが使用されていない場合、 **ssbdiagnose** では、SQLCMDPASSWORD 環境変数の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-219">If the **-U** option is used and the **-P** option is not used, **ssbdiagnose** uses the value from the SQLCMDPASSWORD environment variable.</span></span> <span data-ttu-id="eca5d-220">SQLCMDPASSWORD も設定されていない場合は、 **ssbdiagnose** はユーザーにパスワードを要求します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-220">If SQLCMDPASSWORD is not set either, **ssbdiagnose** prompts the user for a password.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="eca5d-221">SET SQLCMDPASSWORD コマンドを入力する際は、モニターにパスワードが表示されてしまうので注意してください。</span><span class="sxs-lookup"><span data-stu-id="eca5d-221">When you type a SET SQLCMDPASSWORD command, your password will be visible to anyone who can see your monitor.</span></span>  
  
 <span data-ttu-id="eca5d-222">パスワードなしで **-P** オプションが指定されている場合、 **ssbdiagnose** では既定のパスワード (NULL) を使用します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-222">If the **-P** option is specified without a password **ssbdiagnose** uses the default password (NULL).</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] <span data-ttu-id="eca5d-223">詳細については、「[強力なパスワード](../../relational-databases/security/strong-passwords.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eca5d-223">For more information, see [Strong Passwords](../../relational-databases/security/strong-passwords.md).</span></span>  
  
 <span data-ttu-id="eca5d-224">パスワード プロンプトは、次のようにパスワード プロンプトをコンソールに出力することによって表示されます。 `Password:`</span><span class="sxs-lookup"><span data-stu-id="eca5d-224">The password prompt is displayed by printing the password prompt to the console, as follows: `Password:`</span></span>  
  
 <span data-ttu-id="eca5d-225">ユーザーが行った入力は表示されません。</span><span class="sxs-lookup"><span data-stu-id="eca5d-225">User input is hidden.</span></span> <span data-ttu-id="eca5d-226">つまり、入力時には何も表示されず、カーソルが移動しません。</span><span class="sxs-lookup"><span data-stu-id="eca5d-226">This means that nothing is displayed and the cursor stays in position.</span></span>  
  
 <span data-ttu-id="eca5d-227">**-P** オプションが **-E** オプションと共に使用されると、エラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-227">If the **-P** option is used with the **-E** option, an error message is generated.</span></span>  
  
 <span data-ttu-id="eca5d-228">**-P** オプションに複数の引数がある場合は、エラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-228">If the **-P** option is followed by more than one argument, an error message is generated.</span></span>  
  
 <span data-ttu-id="eca5d-229">**-S** *server_name*[\\*instance_name*]</span><span class="sxs-lookup"><span data-stu-id="eca5d-229">**-S** *server_name*[\\*instance_name*]</span></span>  
 <span data-ttu-id="eca5d-230">分析対象の [!INCLUDE[ssDE](../../includes/ssde-md.md)] サービスが格納されている、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] のインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-230">Specifies the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that holds the [!INCLUDE[ssSB](../../includes/sssb-md.md)] services to be analyzed.</span></span>  
  
 <span data-ttu-id="eca5d-231">サーバー上の *の既定のインスタンスに接続するには、* server_name [!INCLUDE[ssDE](../../includes/ssde-md.md)] を指定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-231">Specify *server_name* to connect to the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on that server.</span></span> <span data-ttu-id="eca5d-232">サーバー上のの名前付きインスタンスに接続するには、 *server_name ***\\*** instance_name*を指定し [!INCLUDE[ssDE](../../includes/ssde-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-232">Specify *server_name***\\***instance_name* to connect to a named instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on that server.</span></span> <span data-ttu-id="eca5d-233">**-S** が指定されていない場合、 **ssbdiagnose** では、SQLCMDSERVER 環境変数の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-233">If **-S** is not specified, **ssbdiagnose** uses the value of the SQLCMDSERVER environment variable.</span></span> <span data-ttu-id="eca5d-234">SQLCMDSERVER も設定されていない場合、 **ssbdiagnose** はローカル コンピューター上にある [!INCLUDE[ssDE](../../includes/ssde-md.md)] の既定のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-234">If SQLCMDSERVER is not set either, **ssbdiagnose** connects to the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the local computer.</span></span>  
  
 <span data-ttu-id="eca5d-235">**-d** *database_name*</span><span class="sxs-lookup"><span data-stu-id="eca5d-235">**-d** *database_name*</span></span>  
 <span data-ttu-id="eca5d-236">分析対象の [!INCLUDE[ssSB](../../includes/sssb-md.md)] サービスが格納されているデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-236">Specifies the database that holds the [!INCLUDE[ssSB](../../includes/sssb-md.md)] services to be analyzed.</span></span> <span data-ttu-id="eca5d-237">データベースが存在しない場合は、エラー メッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-237">If the database does not exist, an error message is generated.</span></span> <span data-ttu-id="eca5d-238">**-d** が指定されていない場合、ログインの既定のデータベースのプロパティに指定されたデータベースが既定値になります。</span><span class="sxs-lookup"><span data-stu-id="eca5d-238">If **-d** is not specified, the default is the database specified in the default-database property for your login.</span></span>  
  
 <span data-ttu-id="eca5d-239">**-l** *login_timeout*</span><span class="sxs-lookup"><span data-stu-id="eca5d-239">**-l** *login_timeout*</span></span>  
 <span data-ttu-id="eca5d-240">サーバーへの接続試行がタイムアウトするまでの秒数を指定します。 **-l** が指定されていない場合、 **ssbdiagnose** では、SQLCMDLOGINTIMEOUT 環境変数に設定された値を使用します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-240">Specifies the number of seconds before an attempt to connect to a server times out. If **-l** is not specified, **ssbdiagnose** uses the value set for the SQLCMDLOGINTIMEOUT environment variable.</span></span> <span data-ttu-id="eca5d-241">SQLCMDLOGINTIMEOUT も設定されていない場合、既定のタイムアウトは 30 秒です。</span><span class="sxs-lookup"><span data-stu-id="eca5d-241">If SQLCMDLOGINTIMEOUT is not set either, the default time-out is thirty seconds.</span></span> <span data-ttu-id="eca5d-242">ログイン タイムアウトは、0 ～ 65,534 の数値にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eca5d-242">The login time-out must be a number between 0 and 65534.</span></span> <span data-ttu-id="eca5d-243">指定した値が数値以外の場合、または範囲外の場合、 **ssbdiagnose** はエラー メッセージを生成します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-243">If the value that is supplied is not numeric or does not fall into that range, **ssbdiagnose** generates an error message.</span></span> <span data-ttu-id="eca5d-244">この値に 0 を指定すると、タイムアウトは無制限になります。</span><span class="sxs-lookup"><span data-stu-id="eca5d-244">A value of 0 specifies time-out to be infinite.</span></span>  
  
 <span data-ttu-id="eca5d-245">**-?**</span><span class="sxs-lookup"><span data-stu-id="eca5d-245">**-?**</span></span>  
 <span data-ttu-id="eca5d-246">コマンド ライン ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-246">Displays command line help.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eca5d-247">解説</span><span class="sxs-lookup"><span data-stu-id="eca5d-247">Remarks</span></span>  
 <span data-ttu-id="eca5d-248">**ssbdiagnose** を使用すると、次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-248">Use **ssbdiagnose** to do the following:</span></span>  
  
-   <span data-ttu-id="eca5d-249">新しく構成された [!INCLUDE[ssSB](../../includes/sssb-md.md)] アプリケーションに構成エラーがないことを確認する。</span><span class="sxs-lookup"><span data-stu-id="eca5d-249">Confirm that there are no configuration errors in a newly configured [!INCLUDE[ssSB](../../includes/sssb-md.md)] application.</span></span>  
  
-   <span data-ttu-id="eca5d-250">既存の [!INCLUDE[ssSB](../../includes/sssb-md.md)] アプリケーションの構成を変更した後に構成エラーがないことを確認する。</span><span class="sxs-lookup"><span data-stu-id="eca5d-250">Confirm that there are no configuration errors after changing the configuration of an existing [!INCLUDE[ssSB](../../includes/sssb-md.md)] application.</span></span>  
  
-   <span data-ttu-id="eca5d-251">[!INCLUDE[ssSB](../../includes/sssb-md.md)] データベースをデタッチしてから [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに再アタッチした後に構成エラーがないことを確認する。</span><span class="sxs-lookup"><span data-stu-id="eca5d-251">Confirm that there are no configuration errors after a [!INCLUDE[ssSB](../../includes/sssb-md.md)] database is detached and then reattached to a new instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="eca5d-252">メッセージがサービス間で正常に送信されない場合に構成エラーがあるかどうかを調査する。</span><span class="sxs-lookup"><span data-stu-id="eca5d-252">Research whether there are configuration errors when messages are not successfully transmitted between services.</span></span>  
  
-   <span data-ttu-id="eca5d-253">[!INCLUDE[ssSB](../../includes/sssb-md.md)] の一連のメッセージ交換要素で発生するすべてのエラーに関するレポートを取得する。</span><span class="sxs-lookup"><span data-stu-id="eca5d-253">Get a report of any errors that occur in a set of [!INCLUDE[ssSB](../../includes/sssb-md.md)] conversation elements.</span></span>  
  
## <a name="configuration-reporting"></a><span data-ttu-id="eca5d-254">構成レポート</span><span class="sxs-lookup"><span data-stu-id="eca5d-254">Configuration Reporting</span></span>  
 <span data-ttu-id="eca5d-255">メッセージ交換で使用されている構成を正しく分析するには、メッセージ交換で使用されているオプションと同じオプションを使用する **ssbdiagnose** の構成レポートを実行します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-255">To correctly analyze the configuration used by a conversation, run a **ssbdiagnose** configuration report that uses the same options that are used by the conversation.</span></span> <span data-ttu-id="eca5d-256">メッセージ交換よりも低いレベルのオプションを **ssbdiagnose** に指定すると、 **ssbdiagnose** は、メッセージ交換に必要な条件を報告しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="eca5d-256">If you specify a lower level of options for **ssbdiagnose** than are used by the conversation, **ssbdiagnose** might not report conditions that are required by the conversation.</span></span> <span data-ttu-id="eca5d-257">また、より高いレベルのオプションを **ssbdiagnose**に指定すると、メッセージ交換に必要のない項目を報告する場合があります。</span><span class="sxs-lookup"><span data-stu-id="eca5d-257">If you specify a higher level of options for **ssbdiagnose**, it might report items that are not required by the conversation.</span></span> <span data-ttu-id="eca5d-258">たとえば、同じデータベース内の 2 つのサービス間のメッセージ交換は、ENCPRYPTION OFF を指定して実行できます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-258">For example, a conversation between two services in the same database can be run with ENCPRYPTION OFF.</span></span> <span data-ttu-id="eca5d-259">**ssbdiagnose** を実行してこの 2 つのサービス間の構成を検証する場合でも、既定の設定 ENCRYPTION ON を使用すると、 **ssbdiagnose** は、データベースにマスター キーが存在しないことを報告します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-259">If you run **ssbdiagnose** to validate the configuration between the two services, but use the default ENCRYPTION ON setting, **ssbdiagnose** reports that the database is missing a master key.</span></span> <span data-ttu-id="eca5d-260">マスター キーは、メッセージ交換には必要ありません。</span><span class="sxs-lookup"><span data-stu-id="eca5d-260">A master key is not required for the conversation.</span></span>  
  
 <span data-ttu-id="eca5d-261">**ssbdiagnose** の構成レポートを実行するたびに、1 つの [!INCLUDE[ssSB](../../includes/sssb-md.md)] サービスまたは 1 組のサービスが分析されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-261">The **ssbdiagnose** configuration report analyzes only one [!INCLUDE[ssSB](../../includes/sssb-md.md)] service or a single pair of services every time it is run.</span></span> <span data-ttu-id="eca5d-262">[!INCLUDE[ssSB](../../includes/sssb-md.md)] サービスの複数のペアに関するレポートを作成するには、 **ssbdiagnose** を複数回呼び出す .cmd コマンド ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-262">To report on multiple pairs of [!INCLUDE[ssSB](../../includes/sssb-md.md)] services, build a .cmd command file that calls **ssbdiagnose** multiple times.</span></span>  
  
## <a name="runtime-reporting"></a><span data-ttu-id="eca5d-263">ランタイム レポート</span><span class="sxs-lookup"><span data-stu-id="eca5d-263">Runtime Reporting</span></span>  
 <span data-ttu-id="eca5d-264">-RUNTIME が指定されている場合、 **ssbdiagnose** は **runtimeconnectionoptions** と **baseconnectionoptions** で指定されたすべてのデータベースを検索して、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] ID の一覧を作成します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-264">When -RUNTIME is specified, **ssbdiagnose** searches all databases specified in **runtimeconnectionoptions** and **baseconnectionoptions** to build a list of [!INCLUDE[ssSB](../../includes/sssb-md.md)] IDs.</span></span> <span data-ttu-id="eca5d-265">作成される ID の一覧は、-NEW および -ID で指定する内容によって異なります。</span><span class="sxs-lookup"><span data-stu-id="eca5d-265">The full list of IDs built depends on what is specified for -NEW and -ID:</span></span>  
  
-   <span data-ttu-id="eca5d-266">**-NEW** も **-ID** も指定されていない場合、接続オプションで指定されたすべてのデータベースに関するすべてのメッセージ交換が一覧に含まれます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-266">If neither **-NEW** or **-ID** are specified, the list includes all conversations for all databases specified in the connection options.</span></span>  
  
-   <span data-ttu-id="eca5d-267">**-NEW** が指定されている場合、 **ssbdiagnose** が作成する一覧には、 **ssbdiagnose** の実行後に開始される最初のメッセージ交換の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-267">If **-NEW** is specified, **ssbdiagnose** includes the elements for the first conversation that starts after **ssbdiagnose** is run.</span></span> <span data-ttu-id="eca5d-268">これには、メッセージ交換 ID、および発信先と発信側の両方のメッセージ交換エンドポイントのメッセージ交換ハンドルも含まれます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-268">This includes the conversation ID and the conversation handles for both the target and initiator conversation endpoints.</span></span>  
  
-   <span data-ttu-id="eca5d-269">**-ID** がメッセージ交換ハンドルと共に指定されている場合、そのハンドルのみが一覧に含まれます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-269">If **-ID** is specified with a conversation handle, only that handle is included in the list.</span></span>  
  
-   <span data-ttu-id="eca5d-270">**-ID** がメッセージ交換 ID と共に指定されている場合、そのメッセージ交換 ID と、そのメッセージ交換の両方のエンドポイントのハンドルが一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-270">If **-ID** is specified with a conversation ID, the conversation ID and the handles for both of its conversation endpoints are added to the list.</span></span>  
  
-   <span data-ttu-id="eca5d-271">**-ID** がメッセージ交換グループ ID と共に指定されている場合、そのグループ内のすべてのメッセージ交換 ID とメッセージ交換ハンドルが一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-271">If **-ID** is specified with a conversation group ID, all the conversation IDs and conversation handles in that group are added to the list.</span></span>  
  
 <span data-ttu-id="eca5d-272">接続オプションで対応されていないデータベースの要素は、一覧に含まれません。</span><span class="sxs-lookup"><span data-stu-id="eca5d-272">The list does not include elements from databases that are not covered by the connection options.</span></span> <span data-ttu-id="eca5d-273">たとえば、 **-ID** を使用してメッセージ交換 ID を指定しても、発信先データベースではなく発信側データベースのみに対して **runtimeconnectionoptions** 句を指定するとします。</span><span class="sxs-lookup"><span data-stu-id="eca5d-273">For example, assume that you use **-ID** to specify a conversation ID, but only provide a **runtimeconnectionoptions** clause for the initiator database and not the target database.</span></span> <span data-ttu-id="eca5d-274">**ssbdiagnose** は、発信先のメッセージ交換ハンドルを ID の一覧に含めず、メッセージ交換 ID と、発信側のメッセージ交換ハンドルのみを含めます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-274">**ssbdiagnose** will not include the target conversation handle in its list of IDs, only the conversation ID and the initiator conversation handle.</span></span>  
  
 <span data-ttu-id="eca5d-275">**ssbdiagnose** では、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] runtimeconnectionoptions **と** baseconnectionoptions **に含まれるデータベースの**イベントを監視します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-275">**ssbdiagnose** monitors the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] events from the databases covered by **runtimeconnectionoptions** and **baseconnectionoptions**.</span></span> <span data-ttu-id="eca5d-276">この ssbdiagnose は、ランタイムの一覧に含まれる 1 つ以上の [!INCLUDE[ssSB](../../includes/sssb-md.md)] ID でエラーが発生したことを示す [!INCLUDE[ssSB](../../includes/sssb-md.md)] イベントを検索します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-276">It searches for [!INCLUDE[ssSB](../../includes/sssb-md.md)] events that indicate an error was encountered by one or more of the [!INCLUDE[ssSB](../../includes/sssb-md.md)] IDs in the runtime list.</span></span> <span data-ttu-id="eca5d-277">また、**ssbdiagnose** は、どのメッセージ交換グループにも特に関連付けられていないシステムレベルの [!INCLUDE[ssSB](../../includes/sssb-md.md)] エラー イベントも検索します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-277">**ssbdiagnose** also searches for system-level [!INCLUDE[ssSB](../../includes/sssb-md.md)] error events not specifically associated with any conversation group.</span></span>  
  
 <span data-ttu-id="eca5d-278">**ssbdiagnose** がメッセージ交換エラーを検出すると、このユーティリティは、構成レポートも実行して、そのイベントの根本的な原因の報告を試行します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-278">If **ssbdiagnose** finds conversation errors, the utility will attempt to report on the root cause of the events by also running a configuration report.</span></span> <span data-ttu-id="eca5d-279">**ssbdiagnose** では、データベース内のメタデータを使用して、メッセージ交換で使用されるインスタンス、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] ID、データベース、サービス、およびコントラクトを特定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-279">**ssbdiagnose** uses the metadata in the databases to try to determine the instances, [!INCLUDE[ssSB](../../includes/sssb-md.md)] IDs, databases, services, and contracts used by the conversation.</span></span> <span data-ttu-id="eca5d-280">その後、使用可能なすべての情報を使用して構成レポートを実行します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-280">It then runs a configuration report using all available information.</span></span>  
  
 <span data-ttu-id="eca5d-281">既定では、 **ssbdiagnose** はエラー イベントを報告しません。</span><span class="sxs-lookup"><span data-stu-id="eca5d-281">By default, **ssbdiagnose** does not report error events.</span></span> <span data-ttu-id="eca5d-282">報告するのは、構成チェック時に見つかった根本的な問題だけです。</span><span class="sxs-lookup"><span data-stu-id="eca5d-282">It only reports the underlying issues found during the configuration check.</span></span> <span data-ttu-id="eca5d-283">これにより、報告される情報量が最小限に抑えられるため、根本的な構成の問題に注目することができます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-283">This minimizes the amount of information reported and helps you focus on the underlying configuration issues.</span></span> <span data-ttu-id="eca5d-284">**-SHOWEVENTS** によって検出されたエラー イベントを確認するには、 **ssbdiagnose**を指定します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-284">You can specify **-SHOWEVENTS** to see the error events encountered by **ssbdiagnose**.</span></span>  
  
## <a name="issues-reported-by-ssbdiagnose"></a><span data-ttu-id="eca5d-285">ssbdiagnose によって報告される問題</span><span class="sxs-lookup"><span data-stu-id="eca5d-285">Issues Reported by ssbdiagnose</span></span>  
 <span data-ttu-id="eca5d-286">**ssbdiagnose** が報告する問題は、3 種類に分類されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-286">**ssbdiagnose** reports three classes of issues.</span></span> <span data-ttu-id="eca5d-287">XML 出力ファイルでは、各種類の問題が Issue 要素の異なる型として報告されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-287">In the XML output file, each class of issue is reported as a separate type of the Issue element.</span></span> <span data-ttu-id="eca5d-288">**ssbdiagnose** が報告する 3 種類の問題は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="eca5d-288">The three types of issues reported by **ssbdiagnose** are as follows:</span></span>  
  
 <span data-ttu-id="eca5d-289">**診断**</span><span class="sxs-lookup"><span data-stu-id="eca5d-289">**Diagnosis**</span></span>  
 <span data-ttu-id="eca5d-290">構成上の問題を報告します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-290">Reports a configuration issue.</span></span> <span data-ttu-id="eca5d-291">これには、 **CONFIGURATION** レポートの実行中または **RUNTIME** レポートの構成フェーズ中に見つかった問題が含まれます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-291">This includes issues found either a **CONFIGURATION** report is running, or during the configuration phase of a **RUNTIME** report.</span></span> <span data-ttu-id="eca5d-292">**ssbdiagnose** は、構成上の各問題を一度だけ報告します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-292">**ssbdiagnose** reports each configuration issue one time.</span></span>  
  
 <span data-ttu-id="eca5d-293">**Event**</span><span class="sxs-lookup"><span data-stu-id="eca5d-293">**Event**</span></span>  
 <span data-ttu-id="eca5d-294">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] RUNTIME **レポートの実行中に監視されるメッセージ交換で問題が検出されたことを示す** イベントを報告します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-294">Reports a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] event that indicates a problem was encountered by a conversation being monitored during a **RUNTIME** report.</span></span> <span data-ttu-id="eca5d-295">**ssbdiagnose** は、イベントが生成されるたびにイベントを報告します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-295">**ssbdiagnose** reports events every time they are generated.</span></span> <span data-ttu-id="eca5d-296">複数のメッセージ交換で問題が検出される場合は、イベントが複数回報告されます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-296">Events can be reported multiple times if several conversations encounter the problem.</span></span>  
  
 <span data-ttu-id="eca5d-297">**問題**</span><span class="sxs-lookup"><span data-stu-id="eca5d-297">**Problem**</span></span>  
 <span data-ttu-id="eca5d-298">**ssbdiagnose** で構成分析を完了したり、メッセージ交換を監視したりすることができない場合に、その原因となる問題を報告します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-298">Reports an issue that is preventing **ssbdiagnose** from completing a configuration analysis or from monitoring conversations.</span></span>  
  
## <a name="sqlcmd-environment-variables"></a><span data-ttu-id="eca5d-299">sqlcmd 環境変数</span><span class="sxs-lookup"><span data-stu-id="eca5d-299">sqlcmd Environment Variables</span></span>  
 <span data-ttu-id="eca5d-300">**ssbdiagnose** ユーティリティでは、 **sqlcmd** ユーティリティでも使用されている SQLCMDSERVER、SQLCMDUSER、SQLCMDPASSWORD、および SQLCMDLOGINTIMOUT の各環境変数がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="eca5d-300">The **ssbdiagnose** utility supports the SQLCMDSERVER, SQLCMDUSER, SQLCMDPASSWORD, and SQLCMDLOGINTIMOUT environment variables that are also used by the **sqlcmd** utility.</span></span> <span data-ttu-id="eca5d-301">これらの環境変数を設定するには、コマンド プロンプトの SET コマンドを使用するか、 **sqlcmd** を使用して実行する [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトの **setvar**コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-301">You can set the environment variables either by using the command prompt SET command, or by using the **setvar** command in [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts that you run by using **sqlcmd**.</span></span> <span data-ttu-id="eca5d-302">**sqlcmd** で **setvar**を使用する方法の詳細については、「 [sqlcmd でのスクリプト変数の使用](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eca5d-302">For more information about how to use **setvar** in **sqlcmd**, see [Use sqlcmd with Scripting Variables](../../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="eca5d-303">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="eca5d-303">Permissions</span></span>  
 <span data-ttu-id="eca5d-304">各 **connectionoptions** 句では、 **-E** または **-U** のいずれかで指定されたログインが、 **-S** で指定されたインスタンスの **sysadmin**固定サーバー ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="eca5d-304">In each **connectionoptions** clause, the login specified with either **-E** or **-U** must be a member of the **sysadmin** fixed-server role in the instance specified in **-S**.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="eca5d-305">例</span><span class="sxs-lookup"><span data-stu-id="eca5d-305">Examples</span></span>  
 <span data-ttu-id="eca5d-306">ここでは、コマンド プロンプトでの **ssbdiagnose** の使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-306">This section contains examples of using **ssbdiagnose** at a command prompt.</span></span>  
  
### <a name="a-checking-the-configuration-of-two-services-in-the-same-database"></a><span data-ttu-id="eca5d-307">A.</span><span class="sxs-lookup"><span data-stu-id="eca5d-307">A.</span></span> <span data-ttu-id="eca5d-308">同じデータベース内の 2 つのサービスの構成を確認する</span><span class="sxs-lookup"><span data-stu-id="eca5d-308">Checking the Configuration of Two Services in the Same Database</span></span>  
 <span data-ttu-id="eca5d-309">次の例では、以下の条件に該当する場合に構成レポートを要求する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-309">The following example shows how to request a configuration report when the following are true;</span></span>  
  
-   <span data-ttu-id="eca5d-310">発信側と発信先のサービスが同じデータベース内に格納されている。</span><span class="sxs-lookup"><span data-stu-id="eca5d-310">The initiator and target service are in the same database.</span></span>  
  
-   <span data-ttu-id="eca5d-311">データベースが [!INCLUDE[ssDE](../../includes/ssde-md.md)]の既定のインスタンスに存在する。</span><span class="sxs-lookup"><span data-stu-id="eca5d-311">The database is in the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="eca5d-312">インスタンスが **ssbdiagnose** が実行されるコンピューター上に存在する。</span><span class="sxs-lookup"><span data-stu-id="eca5d-312">The instances is on the same computer on which **ssbdiagnose** is run.</span></span>  
  
 <span data-ttu-id="eca5d-313">ON CONTRACT が指定されていないため、 **ssbdiagnose** ユーティリティは、DEFAULT コントラクトを使用する構成を報告します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-313">The **ssbdiagnose** utility reports the configuration that uses the DEFAULT contract because ON CONTRACT is not specified.</span></span>  
  
```  
ssbdiagnose -E -d MyDatabase CONFIGURATION FROM SERVICE /test/initiator TO SERVICE /test/target  
```  
  
### <a name="b-checking-the-configuration-of-two-services-on-separate-computers-that-use-one-login"></a><span data-ttu-id="eca5d-314">B.</span><span class="sxs-lookup"><span data-stu-id="eca5d-314">B.</span></span> <span data-ttu-id="eca5d-315">異なるコンピューター上の、同じログインを使用する 2 つのサービスの構成を確認する</span><span class="sxs-lookup"><span data-stu-id="eca5d-315">Checking the Configuration of Two Services on Separate Computers That Use One Login</span></span>  
 <span data-ttu-id="eca5d-316">次の例では、異なるコンピューター上に発信側と発信先のサービスが格納されており、そのサービスに同じ Windows 認証ログインを使用してアクセスできる場合に、構成レポートを要求する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-316">The following example shows how to request a configuration report when the initiator and target service are on separate computers, but can be accessed by using the same Windows Authentication login.</span></span>  
  
```  
ssbdiagnose -E CONFIGURATION FROM SERVICE /text/initiator -S InitiatorComputer -d InitiatorDatabase TO SERVICE /test/target -S TargetComputer -d TargetDatabase ON CONTRACT TestContract  
```  
  
### <a name="c-checking-the-configuration-of-two-services-on-separate-computers-that-use-separate-logins"></a><span data-ttu-id="eca5d-317">C.</span><span class="sxs-lookup"><span data-stu-id="eca5d-317">C.</span></span> <span data-ttu-id="eca5d-318">異なるコンピューター上の、個別のログインを使用する 2 つのサービスの構成を確認する</span><span class="sxs-lookup"><span data-stu-id="eca5d-318">Checking the Configuration of Two Services on Separate Computers That Use Separate Logins</span></span>  
 <span data-ttu-id="eca5d-319">次の例では、異なるコンピューター上に発信側と発信先のサービスが格納されており、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各インスタンスに個別の [!INCLUDE[ssDE](../../includes/ssde-md.md)]認証ログインが必要となる場合に、構成レポートを要求する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-319">The following example shows how to request a configuration report when the initiator and target service are on separate computers, and separate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication logins are required for each instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
```  
ssbdiagnose CONFIGURATION FROM SERVICE /text/initiator   
-S InitiatorComputer -U InitiatorLogin -p !wEx23Dvb   
-d InitiatorDatabase TO SERVICE /test/target -S TargetComputer   
-U TargetLogin -p ER!49jiy -d TargetDatabase ON CONTRACT TestContract  
```  
  
### <a name="d-checking-mirrored-service-configurations-on-separate-computers-with-anonymous-encryption"></a><span data-ttu-id="eca5d-320">D.</span><span class="sxs-lookup"><span data-stu-id="eca5d-320">D.</span></span> <span data-ttu-id="eca5d-321">匿名の暗号化を使用している、異なるコンピューター上でミラー化されたサービスの構成を確認する</span><span class="sxs-lookup"><span data-stu-id="eca5d-321">Checking Mirrored Service Configurations on Separate Computers With Anonymous Encryption</span></span>  
 <span data-ttu-id="eca5d-322">次の例では、異なるコンピューター上に発信側と発信先のサービスが格納されており、発信側が名前付きインスタンスにミラー化されている場合に、構成レポートを要求する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-322">The following example shows how to request a configuration report when the initiator and target service are on separate computers and the initiator is mirrored to a named instance.</span></span> <span data-ttu-id="eca5d-323">このレポートでは、サービスが匿名の暗号化を使用するように構成されていることも確認します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-323">The report also verifies that the services are configured to use anonymous encryption.</span></span>  
  
```  
ssbdiagnose -E CONFIGURATION FROM SERVICE /text/initiator   
-S InitiatorComputer -d InitiatorDatabase MIRROR   
-S MirrorComputer/MirrorInstance TO SERVICE /test/target   
-S TargetComputer -d TargetDatabase ON CONTRACT TestContract ENCRYPTION ANONYMOUS  
```  
  
### <a name="e-checking-the-configuration-of-two-contracts"></a><span data-ttu-id="eca5d-324">E.</span><span class="sxs-lookup"><span data-stu-id="eca5d-324">E.</span></span> <span data-ttu-id="eca5d-325">2 つのコントラクトの構成を確認する</span><span class="sxs-lookup"><span data-stu-id="eca5d-325">Checking the Configuration of Two Contracts</span></span>  
 <span data-ttu-id="eca5d-326">次の例では、以下の条件に該当する場合に構成レポートを要求するコマンド ファイルの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-326">The following example shows how to build a command file that requests configuration reports when the following are true:</span></span>  
  
-   <span data-ttu-id="eca5d-327">発信側と発信先のサービスが同じデータベース内に格納されている。</span><span class="sxs-lookup"><span data-stu-id="eca5d-327">The initiator and target service are in the same database.</span></span>  
  
-   <span data-ttu-id="eca5d-328">データベースが [!INCLUDE[ssDE](../../includes/ssde-md.md)]の既定のインスタンスに存在する。</span><span class="sxs-lookup"><span data-stu-id="eca5d-328">The database is in the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="eca5d-329">インスタンスが **ssbdiagnose** が実行されるコンピューター上に存在する。</span><span class="sxs-lookup"><span data-stu-id="eca5d-329">The instance is on the same computer on which **ssbdiagnose** is run.</span></span>  
  
 <span data-ttu-id="eca5d-330">**ssbdiagnose** は、実行されるたびに、同じサービス間で異なるコントラクトの構成を報告します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-330">Each time **ssbdiagnose** is run it reports the configuration for a different contract between the same services.</span></span>  
  
```  
ssbdiagnose -E -d MyDatabase CONFIGURATION FROM SERVICE   
/test/initiator TO SERVICE /test/target ON CONTRACT PayRaiseContract  
ssbdiagnose -E -d MyDatabase CONFIGURATION FROM SERVICE /test/initiator   
TO SERVICE /test/target ON CONTRACT PromotionContract  
```  
  
### <a name="f-monitor-the-status-of-a-specific-conversation-on-the-local-computer-with-a-time-out"></a><span data-ttu-id="eca5d-331">F.</span><span class="sxs-lookup"><span data-stu-id="eca5d-331">F.</span></span> <span data-ttu-id="eca5d-332">タイムアウトが設定された、ローカル コンピューター上の特定のメッセージ交換の状態を監視する</span><span class="sxs-lookup"><span data-stu-id="eca5d-332">Monitor the status of a specific conversation on the local computer with a time out</span></span>  
 <span data-ttu-id="eca5d-333">次の例では、 **ssbdiagnose**を実行しているコンピューターの既定のインスタンスにある同一のデータベースに発信側と発信先のサービスが格納されている場合に、特定のメッセージ交換を監視する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-333">The following example shows how to monitor a specific conversation where the initiator and target services are in the same database in the default instance of the same computer that is running **ssbdiagnose**.</span></span> <span data-ttu-id="eca5d-334">タイムアウト間隔は 20 秒に設定されています。</span><span class="sxs-lookup"><span data-stu-id="eca5d-334">The time-out interval is set to 20 seconds.</span></span>  
  
```  
ssbdiagnose -E -d TestDatabase RUNTIME -ID D68D77A9-B1CF-41BF-A5CE-279ABCAB140D -TIMEOUT 20  
```  
  
### <a name="g-monitor-the-status-of-a-conversation-that-spans-two-computers"></a><span data-ttu-id="eca5d-335">G.</span><span class="sxs-lookup"><span data-stu-id="eca5d-335">G.</span></span> <span data-ttu-id="eca5d-336">2 台のコンピューターにまたがるメッセージ交換の状態を監視する</span><span class="sxs-lookup"><span data-stu-id="eca5d-336">Monitor the status of a conversation that spans two computers</span></span>  
 <span data-ttu-id="eca5d-337">次の例では、異なるコンピューター上に発信側と発信先のサービスが格納されている場合に、特定のメッセージ交換を監視する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-337">The following example shows how to monitor a specific conversation where the initiator and target services are on separate computers.</span></span>  
  
```  
ssbdiagnose RUNTIME -ID D68D77A9-B1CF-41BF-A5CE-279ABCAB140D   
-TIMEOUT 10 CONNECT TO -E -S InitiatorComputer/InitiatorInstance   
-d InitiatorDatabase CONNECT TO -E -S TargetComputer/TargetInstance   
-d TargetDatabase  
```  
  
### <a name="h-monitor-the-status-of-a-conversation-in-two-databases-in-the-same-instance"></a><span data-ttu-id="eca5d-338">H.</span><span class="sxs-lookup"><span data-stu-id="eca5d-338">H.</span></span> <span data-ttu-id="eca5d-339">同じインスタンス内の 2 つのデータベースにあるメッセージ交換の状態を監視する</span><span class="sxs-lookup"><span data-stu-id="eca5d-339">Monitor the status of a conversation in two databases in the same instance</span></span>  
 <span data-ttu-id="eca5d-340">次の例では、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の同じインスタンスにある異なるデータベースに発信側と発信先のサービスが格納されている場合に、特定のメッセージ交換を監視する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-340">The following example shows how to monitor a specific conversation where the initiator and target services are in separate databases in the same instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="eca5d-341">この例では、 **baseconnectionoptions** を使用してインスタンスとログインの情報を指定し、2 つの CONNECT TO 句を使用してデータベースを指定しています。</span><span class="sxs-lookup"><span data-stu-id="eca5d-341">The example uses the **baseconnectionoptions** to specify the instance and login information, and two CONNECT TO clauses to specify the databases.</span></span> <span data-ttu-id="eca5d-342">すべてのランタイム イベントがレポートの出力に含まれるように、-SHOWEVENTS を指定しています。</span><span class="sxs-lookup"><span data-stu-id="eca5d-342">-SHOWEVENTS is specified so that all runtime events are included in the report output.</span></span>  
  
```  
ssbdiagnose -E -S TestComputer/DevTestInstance RUNTIME -SHOWEVENTS   
-ID 5094d4a7-e38c-4c37-da37-1d58b1cb8455 -TIMEOUT 10 CONNECT TO   
-d InitiatorDatabase CONNECT TO -d TargetDatabase  
```  
  
### <a name="i-monitor-the-status-of-two-conversations-between-two-databases"></a><span data-ttu-id="eca5d-343">I.</span><span class="sxs-lookup"><span data-stu-id="eca5d-343">I.</span></span> <span data-ttu-id="eca5d-344">2 つのデータベース間の 2 つのメッセージ交換の状態を監視する</span><span class="sxs-lookup"><span data-stu-id="eca5d-344">Monitor the status of two conversations between two databases</span></span>  
 <span data-ttu-id="eca5d-345">次の例では、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の同じインスタンスにある異なるデータベースに発信側と発信先のサービスが格納されている場合に、2 つのメッセージ交換を監視する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-345">The following example shows how to monitor two conversations where the initiator and target services are in separate databases in the same instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="eca5d-346">この例では、 **baseconnectionoptions** を使用してインスタンスとログインの情報を指定し、2 つの CONNECT TO 句を使用してデータベースを指定しています。</span><span class="sxs-lookup"><span data-stu-id="eca5d-346">The example uses the **baseconnectionoptions** to specify the instance and login information, and two CONNECT TO clauses to specify the databases.</span></span>  
  
```  
ssbdiagnose -E -S TestComputer/DevTestInstance RUNTIME   
-ID 5094d4a7-e38c-4c37-da37-1d58b1cb8455   
-ID 9b293be9-226b-4e22-e169-1d2c2c15be86 -TIMEOUT 10 CONNECT TO   
-d InitiatorDatabase CONNECT TO -d TargetDatabase  
```  
  
### <a name="j-monitor-the-status-of-all-conversations-between-two-databases"></a><span data-ttu-id="eca5d-347">J.</span><span class="sxs-lookup"><span data-stu-id="eca5d-347">J.</span></span> <span data-ttu-id="eca5d-348">2 つのデータベース間のすべてのメッセージ交換の状態を監視する</span><span class="sxs-lookup"><span data-stu-id="eca5d-348">Monitor the status of all conversations between two databases</span></span>  
 <span data-ttu-id="eca5d-349">次の例では、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]の同じインスタンスにある 2 つのデータベース間で行われるすべてのメッセージ交換を監視する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-349">The following example shows how to monitor all the conversation between two databases in the same instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="eca5d-350">この例では、 **baseconnectionoptions** を使用してインスタンスとログインの情報を指定し、2 つの CONNECT TO 句を使用してデータベースを指定しています。</span><span class="sxs-lookup"><span data-stu-id="eca5d-350">The example uses the **baseconnectionoptions** to specify the instance and login information, and two CONNECT TO clauses to specify the databases.</span></span>  
  
```  
ssbdiagnose -E -S TestComputer/DevTestInstance RUNTIME   
-TIMEOUT 10 CONNECT TO -d InitiatorDatabase CONNECT TO   
-d TargetDatabase  
```  
  
### <a name="k-ignore-specific-errors"></a><span data-ttu-id="eca5d-351">K.</span><span class="sxs-lookup"><span data-stu-id="eca5d-351">K.</span></span> <span data-ttu-id="eca5d-352">特定のエラーを無視する</span><span class="sxs-lookup"><span data-stu-id="eca5d-352">Ignore Specific Errors</span></span>  
 <span data-ttu-id="eca5d-353">次の例では、テスト システムで現在アクティブ化を構成している方法で既知のエラー (303 と 304) を無視する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-353">The following example shows how to ignore known errors (303 and 304) in how activation is currently configured in a test system.</span></span>  
  
```  
ssbdiagnose -IGNORE 303 -IGNORE 304 -E -d TestDatabase   
CONFIGURATION FROM SERVICE /test/initiator TO SERVICE /test/target   
ON CONTRACT TextContract  
```  
  
### <a name="l-redirecting-ssbdiagnose-xml-output"></a><span data-ttu-id="eca5d-354">L.</span><span class="sxs-lookup"><span data-stu-id="eca5d-354">L.</span></span> <span data-ttu-id="eca5d-355">ssbdiagnose の XML 出力をリダイレクトする</span><span class="sxs-lookup"><span data-stu-id="eca5d-355">Redirecting ssbdiagnose XML Output</span></span>  
 <span data-ttu-id="eca5d-356">次の例では、 **ssbdiagnose** が出力を XML ファイルとして生成するように要求する方法を示します。この XML ファイルはファイルにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-356">The following example shows how to request that **ssbdiagnose** generate its output as an XML file that is redirected to a file.</span></span> <span data-ttu-id="eca5d-357">その後、TestDiag.xml ファイルをアプリケーションで開いて、 **ssbdiagnose** の XML ファイルを分析およびレポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-357">The TestDiag.xml file can then be opened by an application to analyze or report **ssbdiagnose** XML files.</span></span> <span data-ttu-id="eca5d-358">また、XML Notepad などの一般的な XML エディターで表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="eca5d-358">Or, you can view it from a general XML editor such as XML Notepad.</span></span>  
  
```  
ssbdiagnose -XML -E -d MyDatabase CONFIGURATION FROM SERVICE   
/test/initiator TO SERVICE /test/target > c:\MyDiagnostics\TestDiag.xml  
```  
  
### <a name="m-using-an-environment-variable"></a><span data-ttu-id="eca5d-359">M.</span><span class="sxs-lookup"><span data-stu-id="eca5d-359">M.</span></span> <span data-ttu-id="eca5d-360">環境変数を使用する</span><span class="sxs-lookup"><span data-stu-id="eca5d-360">Using an Environment Variable</span></span>  
 <span data-ttu-id="eca5d-361">次の例では、最初に、サーバー名を保持する SQLCMDSERVER 環境変数を設定し、次に、 **-S** を指定せずに **ssbdiagnose**を実行します。</span><span class="sxs-lookup"><span data-stu-id="eca5d-361">The following example first sets the SQLCMDSERVER environment variable to hold the server name, and then runs **ssbdiagnose** without specifying **-S**.</span></span>  
  
```  
SET SQLCMDSERVER=MyComputer  
ssbdiagnose -XML -E -d MyDatabase CONFIGURATION FROM SERVICE   
/test/initiator TO SERVICE /test/target  
```  
  
## <a name="see-also"></a><span data-ttu-id="eca5d-362">参照</span><span class="sxs-lookup"><span data-stu-id="eca5d-362">See Also</span></span>  
 <span data-ttu-id="eca5d-363">[SQL Server Service Broker (SQL Server Service Broker)](../../database-engine/configure-windows/sql-server-service-broker.md) </span><span class="sxs-lookup"><span data-stu-id="eca5d-363">[SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md) </span></span>  
 <span data-ttu-id="eca5d-364">[BEGIN DIALOG CONVERSATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/begin-dialog-conversation-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eca5d-364">[BEGIN DIALOG CONVERSATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/begin-dialog-conversation-transact-sql) </span></span>  
 <span data-ttu-id="eca5d-365">[CREATE BROKER PRIORITY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-broker-priority-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eca5d-365">[CREATE BROKER PRIORITY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-broker-priority-transact-sql) </span></span>  
 <span data-ttu-id="eca5d-366">[CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eca5d-366">[CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql) </span></span>  
 <span data-ttu-id="eca5d-367">[CREATE CONTRACT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-contract-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eca5d-367">[CREATE CONTRACT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-contract-transact-sql) </span></span>  
 <span data-ttu-id="eca5d-368">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eca5d-368">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="eca5d-369">[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eca5d-369">[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) </span></span>  
 <span data-ttu-id="eca5d-370">[CREATE MESSAGE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-message-type-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eca5d-370">[CREATE MESSAGE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-message-type-transact-sql) </span></span>  
 <span data-ttu-id="eca5d-371">[CREATE QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-queue-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eca5d-371">[CREATE QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-queue-transact-sql) </span></span>  
 <span data-ttu-id="eca5d-372">[CREATE REMOTE SERVICE BINDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-remote-service-binding-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eca5d-372">[CREATE REMOTE SERVICE BINDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-remote-service-binding-transact-sql) </span></span>  
 <span data-ttu-id="eca5d-373">[CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eca5d-373">[CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql) </span></span>  
 <span data-ttu-id="eca5d-374">[CREATE SERVICE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-service-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eca5d-374">[CREATE SERVICE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-service-transact-sql) </span></span>  
 <span data-ttu-id="eca5d-375">[RECEIVE &#40;Transact-SQL&#41;](/sql/t-sql/statements/receive-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eca5d-375">[RECEIVE &#40;Transact-SQL&#41;](/sql/t-sql/statements/receive-transact-sql) </span></span>  
 <span data-ttu-id="eca5d-376">[sys.transmission_queue &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-transmission-queue-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eca5d-376">[sys.transmission_queue &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-transmission-queue-transact-sql) </span></span>  
 <span data-ttu-id="eca5d-377">[sys.conversation_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eca5d-377">[sys.conversation_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql) </span></span>  
 [<span data-ttu-id="eca5d-378">sys.conversation_groups &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eca5d-378">sys.conversation_groups &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-conversation-groups-transact-sql)  
  
  
