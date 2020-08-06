---
title: ユーザーのアクセス許可のテスト (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 83a03b85-ea7f-4b4a-b19b-f7eca534ffae
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8c109eebb4bf06bf7605ca3b7b5930ce18951e41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641710"
---
# <a name="test-a-user39s-permissions-master-data-services"></a><span data-ttu-id="ecbfd-102">ユーザーのアクセス許可のテスト (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="ecbfd-102">Test a User&#39;s Permissions (Master Data Services)</span></span>
  <span data-ttu-id="ecbfd-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、テスト ユーザーを作成し、Web アプリケーションにログインして権限をテストできます。ユーザーが [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] の URL にアクセスを試みると、ユーザーの資格情報が認証されます。</span><span class="sxs-lookup"><span data-stu-id="ecbfd-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can create a test user and log into the web application to test permissions.When a user attempts to access the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] URL, the user's credentials are authenticated.</span></span> <span data-ttu-id="ecbfd-104">Internet Explorer のセキュリティ設定によって、自動認証を行うかユーザー名とパスワードの入力を求めるかが制御されます。</span><span class="sxs-lookup"><span data-stu-id="ecbfd-104">In Internet Explorer, security settings control whether this occurs automatically or if the user must enter a user name and password.</span></span> <span data-ttu-id="ecbfd-105">これらの設定を変更するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ecbfd-105">To change these settings, complete the following steps:</span></span>  
  
### <a name="to-test-a-users-security"></a><span data-ttu-id="ecbfd-106">ユーザーのセキュリティをテストするには</span><span class="sxs-lookup"><span data-stu-id="ecbfd-106">To test a user's security</span></span>  
  
1.  <span data-ttu-id="ecbfd-107">Internet Explorer 7 以降で、 **[ツール]**、 **[インターネット オプション]** の順にクリックして、 **[セキュリティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ecbfd-107">In Internet Explorer 7 and later, click **Tools**, **Internet Options**, and then click the **Security** tab.</span></span>  
  
2.  <span data-ttu-id="ecbfd-108">**[ローカル イントラネット]** をクリックして、 **[レベルのカスタマイズ]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ecbfd-108">Click **Local Intranet** and then the **Custom Level** button.</span></span>  
  
3.  <span data-ttu-id="ecbfd-109">**[ユーザー認証]** セクションで **[ユーザー名とパスワードを入力してログオンする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ecbfd-109">In the **User Authentication** section, choose **Prompt for user name and password**.</span></span>  
  
4.  <span data-ttu-id="ecbfd-110">次にブラウザー ウィンドウを開くときに、ユーザー名とパスワードの入力を求められます。</span><span class="sxs-lookup"><span data-stu-id="ecbfd-110">The next time you open the browser window, you will be prompted for a user name and password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecbfd-111">参照</span><span class="sxs-lookup"><span data-stu-id="ecbfd-111">See Also</span></span>  
 [<span data-ttu-id="ecbfd-112">セキュリティ (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="ecbfd-112">Security &#40;Master Data Services&#41;</span></span>](security-master-data-services.md)  
  
  
