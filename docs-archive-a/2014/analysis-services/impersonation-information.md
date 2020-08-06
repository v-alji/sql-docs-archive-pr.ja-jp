---
title: 権限借用情報 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 42319d60-ccd0-46b8-af0b-f0968c390d8a
author: minewiskan
ms.author: owend
ms.openlocfilehash: f9226fdbe8656aecf0f9173976c67ee386040d6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712605"
---
# <a name="impersonation-information"></a><span data-ttu-id="ee544-102">[権限借用情報]</span><span class="sxs-lookup"><span data-stu-id="ee544-102">Impersonation Information</span></span>
  <span data-ttu-id="ee544-103">**[権限借用情報]** ページを使用して、Analysis Services がデータ ソースに接続する際に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="ee544-103">Use the **Impersonation Information** page to specify the credentials that Analysis Services will use to connect to the data source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ee544-104">Options</span><span class="sxs-lookup"><span data-stu-id="ee544-104">Options</span></span>  
 <span data-ttu-id="ee544-105">**[特定の Windows ユーザー名とパスワードを使用する]**</span><span class="sxs-lookup"><span data-stu-id="ee544-105">**Use a specific Windows user name and password**</span></span>  
 <span data-ttu-id="ee544-106">このオプションを選択すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトにより、指定の Windows ユーザー アカウントのセキュリティ資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ee544-106">Select this option to have the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object use the security credentials of a specified Windows user account.</span></span> <span data-ttu-id="ee544-107">処理、ROLAP クエリ、不一致バインド、ローカル キューブ、マイニング モデル、リモート パーティション、リンク オブジェクト、ターゲットからソースへの同期に、指定した資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ee544-107">The specified credentials will be used for processing, ROLAP queries, out-of-line bindings, local cubes, mining models, remote partitions, linked objects, and synchronization from target to source.</span></span> <span data-ttu-id="ee544-108">ただし、データ マイニング拡張機能 (DMX) の OPENQUERY ステートメントについては、このオプションが無視され、現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ee544-108">However, for Data Mining Extensions (DMX) OPENQUERY statements, this option is ignored and the credentials of the current user will be used.</span></span>  
  
 <span data-ttu-id="ee544-109">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="ee544-109">**User name**</span></span>  
 <span data-ttu-id="ee544-110">選択した [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトで使用するユーザー アカウントのドメインと名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="ee544-110">Type the domain and name of the user account to be used by the selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span> <span data-ttu-id="ee544-111">次の形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="ee544-111">Use the following format:</span></span>  
  
 <span data-ttu-id="ee544-112">*\<Domain name>* **\\** *\<User account name>*</span><span class="sxs-lookup"><span data-stu-id="ee544-112">*\<Domain name>* **\\** *\<User account name>*</span></span>  
  
 <span data-ttu-id="ee544-113">このオプションは、 **[特定のユーザー名とパスワードを使用する]** がオンになっている場合にのみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="ee544-113">This option is enabled only if **Use a specific name and password** is selected.</span></span>  
  
 <span data-ttu-id="ee544-114">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="ee544-114">**Password**</span></span>  
 <span data-ttu-id="ee544-115">選択した [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトで使用するユーザー アカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="ee544-115">Type the password of the user account to be used by the selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="ee544-116">このオプションは、 **[特定のユーザー名とパスワードを使用する]** がオンになっている場合にのみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="ee544-116">This option is enabled only if **Use a specific name and password** is selected.</span></span>  
  
 <span data-ttu-id="ee544-117">**[サービス アカウントを使用する]**</span><span class="sxs-lookup"><span data-stu-id="ee544-117">**Use the service account**</span></span>  
 <span data-ttu-id="ee544-118">このオプションを選択すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトを管理する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サービスに関連付けられているセキュリティ資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ee544-118">Select this option to have the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object use the security credentials associated with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] service that manages the object.</span></span> <span data-ttu-id="ee544-119">処理、ROLAP クエリ、リモート パーティション、リンク オブジェクト、ターゲットからソースへの同期に、サービス アカウント資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ee544-119">The service account credentials will be used for processing, ROLAP queries, remote partitions, linked objects, and synchronization from target to source.</span></span> <span data-ttu-id="ee544-120">ただし、データ マイニング拡張機能 (DMX) の OPENQUERY ステートメントでは、ローカル キューブとマイニング モデルに現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ee544-120">However, for Data Mining Extensions (DMX) OPENQUERY statements, local cubes, and mining models, the credentials of the current user will be used.</span></span> <span data-ttu-id="ee544-121">不一致バインドに対しては、このオプションはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="ee544-121">This option is not supported for out-of-line bindings.</span></span>  
  
 <span data-ttu-id="ee544-122">**[現在のユーザーの資格情報を使用する]**</span><span class="sxs-lookup"><span data-stu-id="ee544-122">**Use the credentials of the current user**</span></span>  
 <span data-ttu-id="ee544-123">このオプションを選択すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトにより、不一致バインド、DMX OPENQUERY、ローカル キューブ、マイニング モデルに現在のユーザーのセキュリティ資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ee544-123">Select this option to have the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object use the security credentials of the current user for out-of-line bindings, DMX OPENQUERY, local cubes, and mining models.</span></span> <span data-ttu-id="ee544-124">処理、ROLAP クエリ、リモート パーティション、リンク オブジェクト、ターゲットからソースへの同期に対しては、このオプションはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="ee544-124">This option is not supported for processing, ROLAP queries, remote partitions, linked objects, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="ee544-125">**識別子**</span><span class="sxs-lookup"><span data-stu-id="ee544-125">**Inherit**</span></span>  
 <span data-ttu-id="ee544-126">このオプションを選択すると、データベース レベルで定義されている権限借用の動作が使用されます。この動作は、サーバー管理者が `DataSourceImpersonation` データベース プロパティを使用して設定します。</span><span class="sxs-lookup"><span data-stu-id="ee544-126">Select this option to use the impersonation behavior, defined at the database level, which has been set by the server administrator using the `DataSourceImpersonation` database property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee544-127">参照</span><span class="sxs-lookup"><span data-stu-id="ee544-127">See Also</span></span>  
 <span data-ttu-id="ee544-128">[多次元モデルのデータソース](multidimensional-models/data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="ee544-128">[Data Sources in Multidimensional Models](multidimensional-models/data-sources-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="ee544-129">SSAS 多次元&#41;&#40;サポートされるデータソース</span><span class="sxs-lookup"><span data-stu-id="ee544-129">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  
