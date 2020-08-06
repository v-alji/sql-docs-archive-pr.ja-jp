---
title: Web サービス タスク | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicetask.f1
helpviewer_keywords:
- Web Service task [Integration Services]
ms.assetid: 5c7206f1-7d6a-4923-8dff-3c4912da4157
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a2f719a6fb0076a3bb286865199a9cf6a008d32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633256"
---
# <a name="web-service-task"></a><span data-ttu-id="ecec2-102">Web サービス タスク</span><span class="sxs-lookup"><span data-stu-id="ecec2-102">Web Service Task</span></span>
  <span data-ttu-id="ecec2-103">Web サービス タスクは、Web サービス メソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ecec2-103">The Web Service task executes a Web service method.</span></span> <span data-ttu-id="ecec2-104">Web サービス タスクは、次の目的で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ecec2-104">You can use the Web Service task for the following purposes:</span></span>  
  
-   <span data-ttu-id="ecec2-105">Web サービス メソッドが返す値を変数に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="ecec2-105">Writing to a variable the values that a Web service method returns.</span></span> <span data-ttu-id="ecec2-106">たとえば、Web サービス メソッドから 1 日の最高気温を取得し、その値を使用して、列の値を設定する式で使用する変数を更新できます。</span><span class="sxs-lookup"><span data-stu-id="ecec2-106">For example, you could obtain the highest temperature of the day from a Web service method, and then use that value to update a variable that is used in an expression that sets a column value.</span></span>  
  
-   <span data-ttu-id="ecec2-107">Web サービス メソッドが返す値をファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="ecec2-107">Writing to a file the values that a Web service method returns.</span></span> <span data-ttu-id="ecec2-108">たとえば、見込み客の一覧をファイルに書き込み、データをデータベースに書き込む前にそのデータをクリーンにするためのパッケージのデータ ソースとして、そのファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ecec2-108">For example, a list of potential customers can be written to a file and the file then used as a data source in a package that cleans the data before it is written to a database.</span></span>  
  
## <a name="wsdl-file"></a><span data-ttu-id="ecec2-109">WSDL ファイル</span><span class="sxs-lookup"><span data-stu-id="ecec2-109">WSDL File</span></span>  
 <span data-ttu-id="ecec2-110">Web サービス タスクは、HTTP 接続マネージャーを使用して Web サービスに接続します。</span><span class="sxs-lookup"><span data-stu-id="ecec2-110">The Web Service task uses an HTTP connection manager to connect to the Web service.</span></span> <span data-ttu-id="ecec2-111">HTTP 接続マネージャーは、Web サービス タスクとは別に構成され、タスク内で参照されます。</span><span class="sxs-lookup"><span data-stu-id="ecec2-111">The HTTP connection manager is configured separately from the Web Service task, and is referenced in the task.</span></span> <span data-ttu-id="ecec2-112">HTTP 接続マネージャーは、サーバーの URL、Web サービスのサーバーにアクセスするための資格情報、タイムアウト長などの、サーバーのプロキシ設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="ecec2-112">The HTTP connection manager specifies the server proxy settings such as the server URL, credentials for accessing the Web services server, and time-out length.</span></span> <span data-ttu-id="ecec2-113">詳細については、「 [HTTP 接続マネージャー](../connection-manager/http-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ecec2-113">For more information, see [HTTP Connection Manager](../connection-manager/http-connection-manager.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ecec2-114">HTTP 接続マネージャーでは、匿名認証と基本認証のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ecec2-114">The HTTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="ecec2-115">Windows 認証はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ecec2-115">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="ecec2-116">HTTP 接続マネージャーは、Web サイトまたは Web サービス記述言語 (WSDL) ファイルを参照できます。</span><span class="sxs-lookup"><span data-stu-id="ecec2-116">The HTTP connection manager can point to a Web site or to a Web Service Description Language (WSDL) file.</span></span> <span data-ttu-id="ecec2-117">WSDL ファイルを参照する HTTP 接続マネージャーの URL には、 `?WSDL` パラメーターが含まれます。たとえば、 `http://MyServer/MyWebService/MyPage.asmx?WSDL`と指定します。</span><span class="sxs-lookup"><span data-stu-id="ecec2-117">The URL of the HTTP connection manager that points to a WSDL file includes the `?WSDL` parameter: for example, `http://MyServer/MyWebService/MyPage.asmx?WSDL`.</span></span>  
  
 <span data-ttu-id="ecec2-118">**デザイナーで用意されている** [Web サービス タスク エディター] [!INCLUDE[ssIS](../../includes/ssis-md.md)] ダイアログ ボックスを使用して Web サービス タスクを構成するには、WSDL ファイルがローカルで使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecec2-118">The WSDL file must be available locally to configure the Web Service task using the **Web Service Task Editor** dialog box that [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides.</span></span>  
  
-   <span data-ttu-id="ecec2-119">HTTP 接続マネージャーが Web サイトを参照する場合、WSDL ファイルを手動でローカル コンピューターにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecec2-119">If the HTTP connection manager points to a Web site, the WSDL file must be copied manually to a local computer.</span></span>  
  
-   <span data-ttu-id="ecec2-120">HTTP 接続マネージャーが WSDL ファイルを参照する場合、Web サービス タスクを使用して、Web サイトからその WSDL ファイルをローカル ファイルにダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="ecec2-120">If the HTTP connection manager points to a WSDL file, the file can be downloaded from the Web site to a local file by the Web Service task.</span></span>  
  
 <span data-ttu-id="ecec2-121">WSDL ファイルには、Web サービスが提供するメソッド、メソッドに必要な入力パラメーター、メソッドが返す応答、および Web サービスとの通信方法が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="ecec2-121">The WSDL file lists the methods that the Web service offers, the input parameters that the methods require, the responses that the methods return, and how to communicate with the Web service.</span></span>  
  
 <span data-ttu-id="ecec2-122">メソッドが入力パラメーターを使用する場合、Web サービス タスクにはパラメーター値が必要です。</span><span class="sxs-lookup"><span data-stu-id="ecec2-122">If the method uses input parameters, the Web Service task requires parameter values.</span></span> <span data-ttu-id="ecec2-123">たとえば、身長に基づいて購入するスキーの長さをアドバイスする Web サービス メソッドでは、入力パラメーターに身長を送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecec2-123">For example, a Web service method that recommends the length of skis you should purchase based on your height requires that your height be submitted in an input parameter.</span></span> <span data-ttu-id="ecec2-124">パラメーター値は、タスク内で定義されている文字列、またはタスクのスコープか親コンテナーで定義されている変数によって指定できます。</span><span class="sxs-lookup"><span data-stu-id="ecec2-124">The parameter values can be provided either by strings that are defined in the task, or by variables defined in the scope of the task or a parent container.</span></span> <span data-ttu-id="ecec2-125">変数を使用すると、パッケージ構成またはスクリプトを使用してパラメーター値を動的に更新できるという利点があります。</span><span class="sxs-lookup"><span data-stu-id="ecec2-125">The advantage of using variables is that they let you dynamically update the parameter values by using package configurations or scripts.</span></span> <span data-ttu-id="ecec2-126">詳細については、「[Integration Services (SSIS) の変数](../integration-services-ssis-variables.md)」と「[パッケージ構成](../package-configurations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ecec2-126">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Package Configurations](../package-configurations.md).</span></span>  
  
 <span data-ttu-id="ecec2-127">多くの Web サービス メソッドでは、入力パラメーターを使用しません。</span><span class="sxs-lookup"><span data-stu-id="ecec2-127">Many Web service methods do not use input parameters.</span></span> <span data-ttu-id="ecec2-128">たとえば、今月が誕生月の大統領の名前を取得する Web サービス メソッドでは、入力パラメーターは必要ありません。これは、Web サービスで現在の月をローカルに判別できるためです。</span><span class="sxs-lookup"><span data-stu-id="ecec2-128">For example, a Web service method that gets the names of presidents who were born in the current month would not require an input parameter because the Web service can determine the current month locally.</span></span>  
  
 <span data-ttu-id="ecec2-129">Web サービス メソッドの結果は、変数またはファイルに書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="ecec2-129">The results of the Web service method can be written to a variable or to a file.</span></span> <span data-ttu-id="ecec2-130">結果を書き込むファイルを指定するか、変数の名前を指定するには、ファイル接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="ecec2-130">You use the File connection manager either to specify the file or to provide the name of the variable to write the results to.</span></span> <span data-ttu-id="ecec2-131">詳細については、「[ファイル接続マネージャー](../connection-manager/file-connection-manager.md)」および「[Integration Services (SSIS) の変数](../integration-services-ssis-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ecec2-131">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
## <a name="custom-logging-messages-available-on-the-web-service-task"></a><span data-ttu-id="ecec2-132">Web サービス タスクで使用できるカスタム ログ メッセージ</span><span class="sxs-lookup"><span data-stu-id="ecec2-132">Custom Logging Messages Available on the Web Service Task</span></span>  
 <span data-ttu-id="ecec2-133">次の表は、Web サービス タスクに対して有効にできるカスタム ログ エントリの一覧です。</span><span class="sxs-lookup"><span data-stu-id="ecec2-133">The following table lists the custom log entries that you can enable for the Web Service task.</span></span> <span data-ttu-id="ecec2-134">詳しくは、「[Integration Services &#40;SSIS&#41; のログ記録](../performance/integration-services-ssis-logging.md)」と「[ログ記録用のカスタム メッセージ](../custom-messages-for-logging.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ecec2-134">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="ecec2-135">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="ecec2-135">Log entry</span></span>|<span data-ttu-id="ecec2-136">説明</span><span class="sxs-lookup"><span data-stu-id="ecec2-136">Description</span></span>|  
|---------------|-----------------|  
|`WSTaskBegin`|<span data-ttu-id="ecec2-137">タスクが Web サービスへのアクセスを開始しました。</span><span class="sxs-lookup"><span data-stu-id="ecec2-137">The task began to access a Web service.</span></span>|  
|`WSTaskEnd`|<span data-ttu-id="ecec2-138">タスクが Web サービス メソッドを完了しました。</span><span class="sxs-lookup"><span data-stu-id="ecec2-138">The task completed a Web service method.</span></span>|  
|`WSTaskInfo`|<span data-ttu-id="ecec2-139">タスクに関する説明情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ecec2-139">Descriptive information about the task.</span></span>|  
  
## <a name="configuration-of-the-web-service-task"></a><span data-ttu-id="ecec2-140">Web サービス タスクの構成</span><span class="sxs-lookup"><span data-stu-id="ecec2-140">Configuration of the Web Service Task</span></span>  
 <span data-ttu-id="ecec2-141">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="ecec2-141">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="ecec2-142">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ecec2-142">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="ecec2-143">[Web サービス タスク エディター &#40;[全般] ページ&#41;](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="ecec2-143">[Web Service Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   <span data-ttu-id="ecec2-144">[Web サービス タスク エディター &#40;[入力] ページ&#41;](../web-service-task-editor-input-page.md)</span><span class="sxs-lookup"><span data-stu-id="ecec2-144">[Web Service Task Editor &#40;Input Page&#41;](../web-service-task-editor-input-page.md)</span></span>  
  
-   <span data-ttu-id="ecec2-145">[Web サービス タスク エディター &#40;[出力] ページ&#41;](../web-service-task-editor-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="ecec2-145">[Web Service Task Editor &#40;Output Page&#41;](../web-service-task-editor-output-page.md)</span></span>  
  
-   <span data-ttu-id="ecec2-146">[[式] ページ](../expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="ecec2-146">[Expressions Page](../expressions/expressions-page.md)</span></span>  
  
 <span data-ttu-id="ecec2-147">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ecec2-147">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="ecec2-148">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="ecec2-148">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-web-service-task"></a><span data-ttu-id="ecec2-149">プログラムによる Web サービス タスクの構成</span><span class="sxs-lookup"><span data-stu-id="ecec2-149">Programmatic Configuration of the Web Service Task</span></span>  
 <span data-ttu-id="ecec2-150">プログラムによってこれらのプロパティを設定する方法の詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ecec2-150">For more information about programmatically setting these properties, click one of the following topics:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WebServiceTask.WebServiceTask>  
  
## <a name="related-content"></a><span data-ttu-id="ecec2-151">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="ecec2-151">Related Content</span></span>  
 <span data-ttu-id="ecec2-152">MSDN ライブラリのビデオ「[Web サービス タスクを使用して Web サービスを呼び出す方法 (SQL Server ビデオ)](https://go.microsoft.com/fwlink/?LinkId=259642) (technet.microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="ecec2-152">Video, [How to: Call a Web Service by Using the Web Service Task (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=259642), on technet.microsoft.com.</span></span>  
  
 <span data-ttu-id="ecec2-153">[SSIS パッケージを使用して Web サービスを使用する方法](https://www.c-sharpcorner.com/article/how-to-consume-web-service-through-ssis-package/)。</span><span class="sxs-lookup"><span data-stu-id="ecec2-153">[How To Consume Web Service Through SSIS Package](https://www.c-sharpcorner.com/article/how-to-consume-web-service-through-ssis-package/).</span></span>  
  
  
