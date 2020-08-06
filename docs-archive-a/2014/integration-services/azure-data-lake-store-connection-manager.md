---
title: Azure Data Lake Store 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSCM.F1
- SQL11.DTS.DESIGNER.AFPADLSCM.F1
ms.assetid: 7f1323f9-9dc3-4378-9c70-bbc65bfeabfd
author: yualan
ms.author: chugu
ms.openlocfilehash: 1ab6e90aad6472cc10bbb12cf4ca17def501bf00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740237"
---
# <a name="azure-data-lake-store-connection-manager"></a><span data-ttu-id="6292a-102">Azure Data Lake Store 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="6292a-102">Azure Data Lake Store Connection Manager</span></span>
  <span data-ttu-id="6292a-103">**Azure Data Lake Store 接続マネージャー** では、SSIS パッケージを 2 種類の認証 (Azure AD のユーザー ID および Azure AD のサービス ID) を使用して Azure Data Lake Store サービスに接続することができます。</span><span class="sxs-lookup"><span data-stu-id="6292a-103">The **Azure Data Lake Store connection manager** enables an SSIS package to connect to an Azure Data Lake Store service through two authentication types: Azure AD User Identity and Azure AD Service Identity.</span></span>  

## <a name="configure-the-azure-data-lake-store-connection-manager"></a><span data-ttu-id="6292a-104">Azure Data Lake Store 接続マネージャーを構成する</span><span class="sxs-lookup"><span data-stu-id="6292a-104">Configure the Azure Data Lake Store Connection Manager</span></span> 
  
1.  <span data-ttu-id="6292a-105">**[SSIS 接続マネージャーの追加]** ダイアログ ボックスで **[AzureDataLake]** を選択し、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6292a-105">In the **Add SSIS Connection Manager** dialog box, select **AzureDataLake**, and click **Add**.</span></span>   
  
2.  <span data-ttu-id="6292a-106">Azure Data Lake Store 接続マネージャー エディター ダイアログ ボックスの **[ADLS ホスト]** フィールドに、Azure Data Lake Store ホストの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="6292a-106">In the Azure Data Lake Store Connection Manager Editor dialog box, type in the Azure Data Lake Store host URL in **ADLS Host** field.</span></span> <span data-ttu-id="6292a-107">例: https: \/ /test.azuredatalakestore.net または test.azuredatalakestore.net。</span><span class="sxs-lookup"><span data-stu-id="6292a-107">For example: https:\//test.azuredatalakestore.net or test.azuredatalakestore.net.</span></span>
  
3.  <span data-ttu-id="6292a-108">Azure Data Lake Store データにアクセスするための該当する認証の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="6292a-108">Choose corresponding authentication type to access Azure Data Lake Store data.</span></span>

    1.  <span data-ttu-id="6292a-109">**[Azure AD のユーザー ID]** 認証オプションを選択した場合は、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="6292a-109">If you selected **Azure AD User Identity** authentication option, do the following:</span></span>

        1. <span data-ttu-id="6292a-110">**[ユーザー名]** と **[パスワード]** のフィールドに値を指定します。</span><span class="sxs-lookup"><span data-stu-id="6292a-110">Specify values for the **User Name** and **Password** field.</span></span> 
    
        2. <span data-ttu-id="6292a-111">**[接続テスト]** ボタンをクリックして接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="6292a-111">Click **Test Connection** button to test the connection.</span></span> <span data-ttu-id="6292a-112">自分自身とテナント管理者が SSIS から Azure Data Lake Store データへのアクセスに同意していない場合は、別ウィンドウで表示されるダイアログで **[同意する]** ボタンをクリックし、SSIS から Azure Data Lake Store データへのアクセスに同意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6292a-112">If you and your tenant administrator didn't consent SSIS to access your Azure Data Lake Store data before, you need click **Accept** button to consent SSIS to access your Azure Data Lake Store data in the pop out dialog.</span></span> <span data-ttu-id="6292a-113">この同意エクスペリエンスの詳細については、「 [Azure Active Directory とアプリケーションの統合](https://docs.microsoft.com/azure/active-directory/manage-apps/plan-an-application-integration#integrating-applications-with-azure-ad)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6292a-113">For more information about this consent experience, see [Integrating applications with Azure Active Directory](https://docs.microsoft.com/azure/active-directory/manage-apps/plan-an-application-integration#integrating-applications-with-azure-ad).</span></span>
    
        > [!NOTE] 
        > <span data-ttu-id="6292a-114">Azure AD のユーザー ID 認証オプションでは、多要素認証と Microsoft アカウントはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6292a-114">For Azure AD User Identity authentication option, multi-factor authentication and Microsoft account is NOT supported.</span></span>
    
    2.  <span data-ttu-id="6292a-115">**[Azure AD のサービス ID]** 認証オプションを選択した場合は、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="6292a-115">If you selected **Azure AD Service Identity** authentication option, do the following:</span></span>
        1. <span data-ttu-id="6292a-116">Azure Data Lake リソースにアクセスできる AAD アプリケーションおよびサービス プリンシパルを作成します。</span><span class="sxs-lookup"><span data-stu-id="6292a-116">Create an AAD application and service principal that can access Azure Data Lake resources.</span></span>
    
        2. <span data-ttu-id="6292a-117">Azure Data Lake リソースにアクセスするために適切な権限をこの AAD アプリケーションに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="6292a-117">Assign this AAD application corresponding permissions to access your Azure Data Lake resources.</span></span> <span data-ttu-id="6292a-118">この認証オプションの詳細については、「 [Use portal to create Active Directory application and service principal that can access resources](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal)」 (ポータルを使用して、リソースにアクセスできる Active Directory アプリケーションとサービス プリンシパルを作成する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6292a-118">For more information about this authentication option, see [Use portal to create Active Directory application and service principal that can access resources](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).</span></span>
    
        3. <span data-ttu-id="6292a-119">**[クライアント ID]**、 **[シークレット キー]** および **[テナント名]** の各フィールドに値を指定します。</span><span class="sxs-lookup"><span data-stu-id="6292a-119">Specify values for **Client Id**, **Secret Key** and **Tenant Name** field.</span></span>
    
        4. <span data-ttu-id="6292a-120">**[接続テスト]** ボタンをクリックして接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="6292a-120">Click **Test Connection** button to test the connection.</span></span>  
  
4.  <span data-ttu-id="6292a-121">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="6292a-121">Click **OK** to close the dialog box.</span></span>  
  
    <span data-ttu-id="6292a-122">作成した接続マネージャーのプロパティは、 **[プロパティ]** ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6292a-122">You can see the properties of the connection manager you created in the **Properties** window.</span></span>  
  
  
