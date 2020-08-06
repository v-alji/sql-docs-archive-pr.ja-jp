---
title: Reporting Services での承認 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- authorization [Reporting Services]
ms.assetid: 15fc1c7b-560c-4737-b126-e0d428a1b530
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7420b45175ca0b0a5fc66da4a7939b07b79c75b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641479"
---
# <a name="authorization-in-reporting-services"></a><span data-ttu-id="9bb11-102">Reporting Services での承認</span><span class="sxs-lookup"><span data-stu-id="9bb11-102">Authorization in Reporting Services</span></span>
  <span data-ttu-id="9bb11-103">承認は、レポート サーバー データベースの特定のリソースに対して要求された種類のアクセスに、ID を付与するかどうかを判断する処理です。</span><span class="sxs-lookup"><span data-stu-id="9bb11-103">Authorization is the process of determining whether an identity should be granted the requested type of access to a given resource in the report server database.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="9bb11-104">では、ロールベースの承認アーキテクチャを使用します。つまり、そのアプリケーションでユーザーに割り当てられているロールに基づいて、各リソースにユーザー アクセス権を付与します。</span><span class="sxs-lookup"><span data-stu-id="9bb11-104">uses a role-based authorization architecture that grants a user access to a given resource based on the user's role assignment for the application.</span></span> <span data-ttu-id="9bb11-105">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のセキュリティ拡張機能には、レポート サーバーでユーザーが認証された後、そのユーザーにアクセス権を付与するための承認コンポーネントが実装されています。</span><span class="sxs-lookup"><span data-stu-id="9bb11-105">Security extensions for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] contain an implementation of an authorization component that is used to grant access to users once they are authenticated on the report server.</span></span> <span data-ttu-id="9bb11-106">SOAP API および URL アクセスを使用して、ユーザーがシステムまたはレポート サーバー アイテムに対して操作を実行しようとすると、承認が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9bb11-106">Authorization is invoked when a user attempts to perform an operation on the system or a report server item through the SOAP API and via URL access.</span></span> <span data-ttu-id="9bb11-107">これは、セキュリティ拡張機能のインターフェイス**IAuthorizationExtension**によって可能になります。</span><span class="sxs-lookup"><span data-stu-id="9bb11-107">This is made possible through the security extension interface **IAuthorizationExtension**.</span></span> <span data-ttu-id="9bb11-108">前に説明したように、すべての拡張機能は、配置した拡張機能の基本インターフェイスである **IExtension** から継承されます。</span><span class="sxs-lookup"><span data-stu-id="9bb11-108">As stated previously, all extensions inherit from **IExtension** the base interface for any extension that you deploy.</span></span> <span data-ttu-id="9bb11-109">**Iextension**と**IAuthorizationExtension**は、Microsoft の**サービス**の名前空間のメンバーです。</span><span class="sxs-lookup"><span data-stu-id="9bb11-109">**IExtension** and **IAuthorizationExtension** are members of the **Microsoft.ReportingServices.Interfaces** namespace.</span></span>

## <a name="checking-access"></a><span data-ttu-id="9bb11-110">アクセスのチェック</span><span class="sxs-lookup"><span data-stu-id="9bb11-110">Checking Access</span></span>
 <span data-ttu-id="9bb11-111">承認でカスタム セキュリティの実装に不可欠なのはアクセス チェックです。これは、<xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> メソッドに実装されています。</span><span class="sxs-lookup"><span data-stu-id="9bb11-111">In authorization, the key to any custom security implementation is the access check, which is implemented in the <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> method.</span></span> <span data-ttu-id="9bb11-112"><xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> は、ユーザーがレポート サーバーに対する操作を試行するたびに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9bb11-112"><xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> is called each time a user attempts an operation on the report server.</span></span> <span data-ttu-id="9bb11-113"><xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> メソッドは、操作の種類ごとにオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="9bb11-113">The <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> method is overloaded for each operation type.</span></span> <span data-ttu-id="9bb11-114">フォルダー操作の場合、アクセス チェックの例は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9bb11-114">For folder operations, an example of an access check might look like the following:</span></span>

```
// Overload for Folder operations
public bool CheckAccess(
   string userName, 
   IntPtr userToken, 
   byte[] secDesc, 
   FolderOperation requiredOperation)
{
   // If the user is the administrator, allow unrestricted access.
   if (userName == m_adminUserName) 
      return true;

   AceCollection acl = DeserializeAcl(secDesc);
   foreach(AceStruct ace in acl)
   {
         if (userName == ace.PrincipalName)
         {
            foreach(FolderOperation aclOperation in 
               ace.FolderOperations)
            {
               if (aclOperation == requiredOperation)
                     return true;
            }
         }
   }
   return false;
}
```

 <span data-ttu-id="9bb11-115">レポート サーバーが <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> メソッドを呼び出すときに、ログオンしているユーザーの名前、ユーザー トークン、アイテムのセキュリティ記述子、および要求された操作を渡します。</span><span class="sxs-lookup"><span data-stu-id="9bb11-115">The report server calls the <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> method by passing in the name of the logged-on user, a user token, the security descriptor for the item, and the requested operation.</span></span> <span data-ttu-id="9bb11-116">ユーザー名のセキュリティ記述子をチェックし、要求を実行する適切な権限を持っているか確認します。次に、アクセスが許可されたことを通知するには `true` を、アクセスが拒否されたことを通知するには `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="9bb11-116">Here you would check the security descriptor for the user name and the appropriate permission to complete the request, then return `true` to signify that access is granted or `false` to signify access is denied.</span></span>

## <a name="security-descriptors"></a><span data-ttu-id="9bb11-117">セキュリティ記述子</span><span class="sxs-lookup"><span data-stu-id="9bb11-117">Security Descriptors</span></span>
 <span data-ttu-id="9bb11-118">レポート サーバー データベースのアイテムに対して承認ポリシーを設定する場合は、レポート マネージャーなどのクライアント アプリケーションがユーザー情報をアイテムのセキュリティ ポリシーと一緒にセキュリティ拡張機能に送信します。</span><span class="sxs-lookup"><span data-stu-id="9bb11-118">When setting authorization policies on items in the report server database, a client application (such as Report Manager) submits the user information to the security extension along with a security policy for the item.</span></span> <span data-ttu-id="9bb11-119">このセキュリティ ポリシーとユーザー情報をまとめてセキュリティ記述子と呼びます。</span><span class="sxs-lookup"><span data-stu-id="9bb11-119">This security policy and user information are known collectively as a security descriptor.</span></span> <span data-ttu-id="9bb11-120">セキュリティ記述子には、レポート サーバー データベースのアイテムに関する次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9bb11-120">A security descriptor contains the following information for an item in the report server database:</span></span>

-   <span data-ttu-id="9bb11-121">アイテムで操作を実行する権限を持っているグループまたはユーザー</span><span class="sxs-lookup"><span data-stu-id="9bb11-121">The group or user that has some type of permission to perform operations on the item.</span></span>

-   <span data-ttu-id="9bb11-122">項目の種類。</span><span class="sxs-lookup"><span data-stu-id="9bb11-122">The item's type.</span></span>

-   <span data-ttu-id="9bb11-123">アイテムへのアクセスを制御する任意のアクセス制御リスト</span><span class="sxs-lookup"><span data-stu-id="9bb11-123">A discretionary access control list controlling access to the item.</span></span>

 <span data-ttu-id="9bb11-124">セキュリティ記述子は、Web サービス <xref:ReportService2010.ReportingService2010.SetPolicies%2A> メソッドおよび <xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A> メソッドを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="9bb11-124">Security descriptors are created using the Web service <xref:ReportService2010.ReportingService2010.SetPolicies%2A> and <xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A> methods.</span></span>

### <a name="authorization-flow"></a><span data-ttu-id="9bb11-125">承認フロー</span><span class="sxs-lookup"><span data-stu-id="9bb11-125">Authorization Flow</span></span>
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="9bb11-126">の承認は、サーバーで動作するように構成されているセキュリティ拡張機能によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="9bb11-126">authorization is controlled by the security extension currently configured to run on the server.</span></span> <span data-ttu-id="9bb11-127">承認はロールベースであり、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] セキュリティ アーキテクチャによって指定された権限と操作に限定されます。</span><span class="sxs-lookup"><span data-stu-id="9bb11-127">Authorization is role-based and limited to the permissions and operations supplied by the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] security architecture.</span></span> <span data-ttu-id="9bb11-128">次の図は、レポート サーバー データベースのアイテムを操作するユーザーを承認するプロセスを示しています。</span><span class="sxs-lookup"><span data-stu-id="9bb11-128">The following diagram depicts the process of authorizing users to operate on items in the report server database:</span></span>

 <span data-ttu-id="9bb11-129">![Reporting Services のセキュリティ承認フロー](../../media/rosettasecurityextensionauthorizationflow.gif "Reporting Services のセキュリティ承認フロー")</span><span class="sxs-lookup"><span data-stu-id="9bb11-129">![Reporting Services security authorization flow](../../media/rosettasecurityextensionauthorizationflow.gif "Reporting Services security authorization flow")</span></span>

 <span data-ttu-id="9bb11-130">この図のように、承認は次の順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="9bb11-130">As shown in this diagram, authorization follows this sequence:</span></span>

1.  <span data-ttu-id="9bb11-131">認証が完了すると、クライアント アプリケーションは、Reporting Services Web サービスのメソッドを使用してレポート サーバーに要求を発行します。</span><span class="sxs-lookup"><span data-stu-id="9bb11-131">Once authenticated, client applications make requests to the report server through the Reporting Services Web service methods.</span></span> <span data-ttu-id="9bb11-132">その際、各 Web 要求の HTTP ヘッダーに認証チケットがクッキーとして追加され、レポート サーバーに渡されます。</span><span class="sxs-lookup"><span data-stu-id="9bb11-132">An authentication ticket is passed to the report server in the form of a cookie in the HTTP header of each Web request.</span></span>

2.  <span data-ttu-id="9bb11-133">アクセス チェックの前にクッキーが検証されます。</span><span class="sxs-lookup"><span data-stu-id="9bb11-133">The cookie is validated prior to any access check.</span></span>

3.  <span data-ttu-id="9bb11-134">クッキーの有効性を確認すると、レポート サーバーは <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension.GetUserInfo%2A> を呼び出し、ユーザーに ID を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="9bb11-134">Once the cookie is validated, the report server calls <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension.GetUserInfo%2A> and the user is given an identity.</span></span>

4.  <span data-ttu-id="9bb11-135">ユーザーが Reporting Services Web サービスをとおして操作を試行します。</span><span class="sxs-lookup"><span data-stu-id="9bb11-135">The user attempts an operation through the Reporting Services Web service.</span></span>

5.  <span data-ttu-id="9bb11-136">レポート サーバーが <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9bb11-136">The report server calls the <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> method.</span></span>

6.  <span data-ttu-id="9bb11-137">セキュリティ識別子が取得され、<xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> のカスタム セキュリティ拡張機能に渡されます。</span><span class="sxs-lookup"><span data-stu-id="9bb11-137">The security descriptor is retrieved and passed to a custom security extension implementation of <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A>.</span></span> <span data-ttu-id="9bb11-138">この時点で、ユーザー、グループ、またはコンピューターがアクセス先アイテムのセキュリティ識別子と比較され、要求された操作の実行が許可されます。</span><span class="sxs-lookup"><span data-stu-id="9bb11-138">At this point, the user, group, or computer is compared to the security descriptor of the item being accessed and is authorized to perform the requested operation.</span></span>

7.  <span data-ttu-id="9bb11-139">ユーザーが承認されると、Web サービスが操作を実行し、呼び出し元アプリケーションに応答を返します。</span><span class="sxs-lookup"><span data-stu-id="9bb11-139">If the user is authorized, the Web service performs the operation and returns a response to the calling application.</span></span>


