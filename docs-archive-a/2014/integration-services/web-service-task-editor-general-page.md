---
title: '[Web サービスタスクエディター] ([全般] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.general.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 4d7df283-430d-4f0f-9dd4-5909554cd5eb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dbacf2a2a867ab01039678ff4f43eebac839c11a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644531"
---
# <a name="web-service-task-editor-general-page"></a><span data-ttu-id="f99bb-102">[Web サービス タスク エディター] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="f99bb-102">Web Service Task Editor (General Page)</span></span>
  <span data-ttu-id="f99bb-103">**[Web サービス タスク エディター]** ダイアログ ボックスの **[全般]** ページを使用すると、HTTP 接続マネージャーの指定、Web サービス タスクで使用する WSDL (Web サービス記述言語) ファイルの場所の指定、Web サービス タスクの記述、WSDL ファイルのダウンロードなどの操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="f99bb-103">Use the **General** page of the **Web Services Task Editor** dialog box to specify an HTTP connection manager, specify the location of the Web Services Description Language (WSDL) file the Web Service task uses, describe the Web Services task, and download the WSDL file.</span></span>  
  
 <span data-ttu-id="f99bb-104">このタスクの詳細については、「 [Web サービス タスク](control-flow/web-service-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f99bb-104">For more information about this task, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f99bb-105">Options</span><span class="sxs-lookup"><span data-stu-id="f99bb-105">Options</span></span>  
 <span data-ttu-id="f99bb-106">**[HTTPConnection]**</span><span class="sxs-lookup"><span data-stu-id="f99bb-106">**HTTPConnection**</span></span>  
 <span data-ttu-id="f99bb-107">接続マネージャーを一覧から選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f99bb-107">Select a connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f99bb-108">HTTP 接続マネージャーでは、匿名認証と基本認証のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f99bb-108">The HTTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="f99bb-109">Windows 認証はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f99bb-109">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="f99bb-110">**関連トピック:** [HTTP 接続マネージャー](connection-manager/http-connection-manager.md)、[HTTP 接続マネージャー エディター &#40;[サーバー] ページ&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)</span><span class="sxs-lookup"><span data-stu-id="f99bb-110">**Related Topics:**  [HTTP Connection Manager](connection-manager/http-connection-manager.md), [HTTP Connection Manager Editor &#40;Server Page&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)</span></span>  
  
 <span data-ttu-id="f99bb-111">**[WSDLFile]**</span><span class="sxs-lookup"><span data-stu-id="f99bb-111">**WSDLFile**</span></span>  
 <span data-ttu-id="f99bb-112">コンピューターのローカルにある WSDL ファイルの完全修飾パスを入力するか、参照ボタン ( **[...]** ) をクリックしてファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="f99bb-112">Type the fully qualified path of a WSDL file that is local to the computer, or click the browse button **(...)** and locate this file.</span></span>  
  
 <span data-ttu-id="f99bb-113">WSDL ファイルを既に手動でコンピューターにダウンロードしている場合は、そのファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="f99bb-113">If you have already manually downloaded the WSDL file to the computer, select this file.</span></span> <span data-ttu-id="f99bb-114">ただし、WSDL ファイルをまだダウンロードしていない場合は、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f99bb-114">However, if the WSDL file has not yet been downloaded, follow these steps:</span></span>  
  
-   <span data-ttu-id="f99bb-115">ファイル名拡張子が ".wsdl" の空のファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f99bb-115">Create an empty file that has the ".wsdl" file name extension.</span></span>  
  
-   <span data-ttu-id="f99bb-116">**[WSDLFile]** オプションで、この空のファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="f99bb-116">Select this empty file for the **WSDLFile** option.</span></span>  
  
-   <span data-ttu-id="f99bb-117">**[Overwritewsdlfile]** の値をに設定して、 `True` 空のファイルが実際の WSDL ファイルで上書きされるようにします。</span><span class="sxs-lookup"><span data-stu-id="f99bb-117">Set the value of **OverwriteWSDLFile** to `True` to enable the empty file to be overwritten with the actual WSDL file.</span></span>  
  
-   <span data-ttu-id="f99bb-118">**[WSDL のダウンロード]** をクリックして実際の WSDL ファイルをダウンロードし、空のファイルを上書きします。</span><span class="sxs-lookup"><span data-stu-id="f99bb-118">Click **Download WSDL** to download the actual WSDL file and overwrite the empty file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f99bb-119">**[WSDL のダウンロード]** オプションは、 **[WSDLFile]** ボックスに既存のローカル ファイルの名前を指定するまで有効になりません。</span><span class="sxs-lookup"><span data-stu-id="f99bb-119">The **Download WSDL** option is not enabled until you provide the name of an existing local file in the **WSDLFile** box.</span></span>  
  
 <span data-ttu-id="f99bb-120">**[OverwriteWSDLFile]**</span><span class="sxs-lookup"><span data-stu-id="f99bb-120">**OverwriteWSDLFile**</span></span>  
 <span data-ttu-id="f99bb-121">Web サービス タスクの WSDL ファイルを上書きできるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="f99bb-121">Indicate whether the WSDL file for the Web Service task can be overwritten.</span></span>  
  
 <span data-ttu-id="f99bb-122">[ **Wsdl のダウンロード**] ボタンを使用して wsdl ファイルをダウンロードする場合は、この値をに設定 `True` します。</span><span class="sxs-lookup"><span data-stu-id="f99bb-122">If you intend to download the WSDL file by using the **Download WSDL** button, set this value to `True`.</span></span>  
  
 <span data-ttu-id="f99bb-123">**名前**</span><span class="sxs-lookup"><span data-stu-id="f99bb-123">**Name**</span></span>  
 <span data-ttu-id="f99bb-124">Web サービス タスクの一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f99bb-124">Provide a unique name for the Web Service task.</span></span> <span data-ttu-id="f99bb-125">この名前は、タスク アイコンのラベルとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="f99bb-125">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f99bb-126">タスク名はパッケージ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99bb-126">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="f99bb-127">**説明**</span><span class="sxs-lookup"><span data-stu-id="f99bb-127">**Description**</span></span>  
 <span data-ttu-id="f99bb-128">Web サービス タスクの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="f99bb-128">Type a description of the Web Service task.</span></span>  
  
 <span data-ttu-id="f99bb-129">**[WSDL のダウンロード]**</span><span class="sxs-lookup"><span data-stu-id="f99bb-129">**Download WSDL**</span></span>  
 <span data-ttu-id="f99bb-130">WSDL ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="f99bb-130">Download the WSDL file.</span></span>  
  
 <span data-ttu-id="f99bb-131">このボタンは、 **[WSDLFile]** ボックスに既存のローカル ファイルの名前を指定するまで有効になりません。</span><span class="sxs-lookup"><span data-stu-id="f99bb-131">This button is not enabled until you provide the name of an existing local file in the **WSDLFile** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f99bb-132">参照</span><span class="sxs-lookup"><span data-stu-id="f99bb-132">See Also</span></span>  
 <span data-ttu-id="f99bb-133">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f99bb-133">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="f99bb-134">[[Web サービスタスクエディター] &#40;入力ページ&#41;](../../2014/integration-services/web-service-task-editor-input-page.md) </span><span class="sxs-lookup"><span data-stu-id="f99bb-134">[Web Service Task Editor &#40;Input Page&#41;](../../2014/integration-services/web-service-task-editor-input-page.md) </span></span>  
 <span data-ttu-id="f99bb-135">[Web サービスタスクエディター &#40;出力ページ&#41;](../../2014/integration-services/web-service-task-editor-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="f99bb-135">[Web Service Task Editor &#40;Output Page&#41;](../../2014/integration-services/web-service-task-editor-output-page.md) </span></span>  
 <span data-ttu-id="f99bb-136">[[式] ページ](expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="f99bb-136">[Expressions Page](expressions/expressions-page.md)</span></span>  
  
  
