---
title: OData 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3caa4372-aff3-4c0f-9ecd-97870948b8d0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 46eedaa008b284661fd1d364d2e2bc87c373a9f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642229"
---
# <a name="odata-connection-manager"></a><span data-ttu-id="4c37e-102">OData 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="4c37e-102">OData Connection Manager</span></span>
  <span data-ttu-id="4c37e-103">OData 接続マネージャーを使用すると、パッケージは OData ソースに接続できます。</span><span class="sxs-lookup"><span data-stu-id="4c37e-103">An OData connection manager enables a package to connect to an OData source.</span></span> <span data-ttu-id="4c37e-104">OData ソース コンポーネントは OData 接続マネージャーを使用して OData ソースに接続し、サービスから取得したデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="4c37e-104">An OData Source component connects to an OData source using an OData connection manager and consumes data from the service.</span></span> <span data-ttu-id="4c37e-105">これらのコンポーネントのインストール手順などの詳細については、「 [OData ソース](../data-flow/odata-source.md)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c37e-105">See [OData Source](../data-flow/odata-source.md)section for detailed information including the installation instructions for these components.</span></span>  
  
## <a name="adding-connection-manager-to-an-ssis-package"></a><span data-ttu-id="4c37e-106">SSIS パッケージへの接続マネージャーの追加</span><span class="sxs-lookup"><span data-stu-id="4c37e-106">Adding Connection Manager to an SSIS Package</span></span>  
 <span data-ttu-id="4c37e-107">次の 3 とおりの方法で、SSIS パッケージに新しい OData 接続マネージャーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="4c37e-107">You can add a new OData Connection Manager to an SSIS package in three ways:</span></span>  
  
-   <span data-ttu-id="4c37e-108">**[OData ソース エディター]** の **[新規]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c37e-108">Click the **New...** button in the **OData Source Editor**</span></span>  
  
-   <span data-ttu-id="4c37e-109">**ソリューションエクスプローラー**で [**接続マネージャー** ] フォルダーを右クリックし、[**新しい接続マネージャー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c37e-109">Right-click **Connection Managers** folder in the **Solution Explorer** and click **New Connection Manager**.</span></span> <span data-ttu-id="4c37e-110">**[接続マネージャーの種類]** の **[ODATA]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c37e-110">Select **ODATA** for **Connection manager type**.</span></span>  
  
-   <span data-ttu-id="4c37e-111">パッケージデザイナーの下部にある [**接続マネージャー** ] ペインを右クリックし、[**新しい接続**] を選択します。[**接続マネージャーの種類**] で [ **ODATA** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4c37e-111">Right-click in the **Connection Managers** pane at the bottom of the package designer, and select **New Connection...**. Select **ODATA** for **Connection manager type**.</span></span>  
  
## <a name="connection-manager-authentication"></a><span data-ttu-id="4c37e-112">接続マネージャーの認証</span><span class="sxs-lookup"><span data-stu-id="4c37e-112">Connection Manager Authentication</span></span>  
 <span data-ttu-id="4c37e-113">OData 接続マネージャーでは、2 つの認証モードがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4c37e-113">The OData Connection Manager supports two modes of authentication.</span></span>  
  
-   <span data-ttu-id="4c37e-114">Windows 認証</span><span class="sxs-lookup"><span data-stu-id="4c37e-114">Windows Authentication</span></span>  
  
-   <span data-ttu-id="4c37e-115">基本認証 (ユーザー名とパスワード)</span><span class="sxs-lookup"><span data-stu-id="4c37e-115">Basic Authentication (username/password)</span></span>  
  
 <span data-ttu-id="4c37e-116">匿名アクセスを使用するには、[Windows 認証] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="4c37e-116">For anonymous access, select the Windows Authentication option</span></span>  
  
### <a name="specifying-and-securing-credentials"></a><span data-ttu-id="4c37e-117">資格情報の指定とセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="4c37e-117">Specifying and Securing Credentials</span></span>  
 <span data-ttu-id="4c37e-118">OData サービスで基本認証が必要な場合は、 [Odata 接続マネージャーエディター](../odata-connection-manager-editor.md)でユーザー名とパスワードを指定できます。</span><span class="sxs-lookup"><span data-stu-id="4c37e-118">If your OData service requires basic authentication, you can specify a username and password in the [OData Connection Manager Editor](../odata-connection-manager-editor.md).</span></span> <span data-ttu-id="4c37e-119">エディターに入力した値は、パッケージ内に保存されます。</span><span class="sxs-lookup"><span data-stu-id="4c37e-119">The values you enter in the editor are persisted in the package.</span></span> <span data-ttu-id="4c37e-120">パスワードの値は、パッケージの保護レベルに応じて暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="4c37e-120">The password value is encrypted according to the package protection level.</span></span>  
  
 <span data-ttu-id="4c37e-121">ユーザー名とパスワードの値を外部化またはパラメーター化する複数の方法があります。</span><span class="sxs-lookup"><span data-stu-id="4c37e-121">There are multiple ways to externalize/parameterize the username and password values.</span></span> <span data-ttu-id="4c37e-122">[!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] でこの作業を実行する 2 つの主要な方法は、パラメーターを使用するか、SQL Server Management Studio を使用してパッケージを実行するときに接続マネージャーのプロパティを直接設定することです。</span><span class="sxs-lookup"><span data-stu-id="4c37e-122">The two primary ways of doing this in [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] are by using parameters, or by setting the connection manager properties directly when you run the package using SQL Server Management Studio.</span></span>  
  
## <a name="odata-connection-manager-properties"></a><span data-ttu-id="4c37e-123">OData 接続マネージャーのプロパティ</span><span class="sxs-lookup"><span data-stu-id="4c37e-123">OData Connection Manager Properties</span></span>  
 <span data-ttu-id="4c37e-124">次の一覧で、変更する可能性のある OData 接続マネージャーのプロパティの一部を説明します。</span><span class="sxs-lookup"><span data-stu-id="4c37e-124">The following list describes some of the OData Connection Manager properties that you may want to change.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4c37e-125">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4c37e-125">Property</span></span>|<span data-ttu-id="4c37e-126">説明</span><span class="sxs-lookup"><span data-stu-id="4c37e-126">Description</span></span>|  
|<span data-ttu-id="4c37e-127">url</span><span class="sxs-lookup"><span data-stu-id="4c37e-127">Url</span></span>|<span data-ttu-id="4c37e-128">サービス ドキュメントに対応する URL。</span><span class="sxs-lookup"><span data-stu-id="4c37e-128">URL to the service document.</span></span>|  
|<span data-ttu-id="4c37e-129">UserName</span><span class="sxs-lookup"><span data-stu-id="4c37e-129">UserName</span></span>|<span data-ttu-id="4c37e-130">基本認証で使用するユーザー名。</span><span class="sxs-lookup"><span data-stu-id="4c37e-130">Username to use for Basic Authentication.</span></span>|  
|<span data-ttu-id="4c37e-131">Password</span><span class="sxs-lookup"><span data-stu-id="4c37e-131">Password</span></span>|<span data-ttu-id="4c37e-132">基本認証で使用するパスワード。</span><span class="sxs-lookup"><span data-stu-id="4c37e-132">Password to use for Basic Authentication.</span></span>|  
|<span data-ttu-id="4c37e-133">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="4c37e-133">ConnectionString</span></span>|<span data-ttu-id="4c37e-134">接続マネージャーの他のプロパティを反映します。</span><span class="sxs-lookup"><span data-stu-id="4c37e-134">Reflects other properties of the connection manager.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c37e-135">参照</span><span class="sxs-lookup"><span data-stu-id="4c37e-135">See Also</span></span>  
 <span data-ttu-id="4c37e-136">[[OData 接続マネージャー エディター]](../odata-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="4c37e-136">[OData Connection Manager Editor](../odata-connection-manager-editor.md)</span></span>  
  
  
