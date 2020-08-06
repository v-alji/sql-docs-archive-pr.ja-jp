---
title: Reporting Services での認証 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], authentication
- forms-based authentication [Reporting Services]
- authentication [Reporting Services]
- custom authentication [Reporting Services]
ms.assetid: 103ce1f9-31d8-44bb-b540-2752e4dcf60b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 59e97ba6ef849d8b4bfddfd6953c85826e351d6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641488"
---
# <a name="authentication-in-reporting-services"></a><span data-ttu-id="3de31-102">Reporting Services での認証</span><span class="sxs-lookup"><span data-stu-id="3de31-102">Authentication in Reporting Services</span></span>
  <span data-ttu-id="3de31-103">認証とは、ユーザーの本人性を立証するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="3de31-103">Authentication is the process of establishing a user's right to an identity.</span></span> <span data-ttu-id="3de31-104">ユーザー認証にはさまざまな方法がありますが、</span><span class="sxs-lookup"><span data-stu-id="3de31-104">There are many techniques that you can use to authenticate a user.</span></span> <span data-ttu-id="3de31-105">最も一般的なのはユーザー パスワードを使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="3de31-105">The most common way is to use passwords.</span></span> <span data-ttu-id="3de31-106">たとえば、フォーム認証を実装する場合は、ユーザーに対して資格情報の提示を要求し (通常は、ログイン名とパスワードを要求するインターフェイスを使用)、データベース テーブルや構成ファイルなどのデータ ストアと照合して、そのユーザーが本人かどうかを検証します。</span><span class="sxs-lookup"><span data-stu-id="3de31-106">When you implement Forms Authentication, for example, you want an implementation that queries users for credentials (usually by some interface that requests a login name and password) and then validates users against a data store, such as a database table or configuration file.</span></span> <span data-ttu-id="3de31-107">資格情報の有効性を確認できない場合は、認証プロセスが失敗し、そのユーザーは匿名ユーザーであると見なされます。</span><span class="sxs-lookup"><span data-stu-id="3de31-107">If the credentials can't be validated, the authentication process fails and the user will assume an anonymous identity.</span></span>  
  
## <a name="custom-authentication-in-reporting-services"></a><span data-ttu-id="3de31-108">Reporting Services でのカスタム認証</span><span class="sxs-lookup"><span data-stu-id="3de31-108">Custom Authentication in Reporting Services</span></span>  
 <span data-ttu-id="3de31-109">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] では、統合セキュリティを使用するか、またはユーザーの資格情報を明示的に受信して検証することによって、Windows オペレーティング システムがユーザー認証を実施します。</span><span class="sxs-lookup"><span data-stu-id="3de31-109">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], the Windows operating system handles the authentication of users either through integrated security or through the explicit reception and validation of user credentials.</span></span> <span data-ttu-id="3de31-110">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] では、カスタム認証を開発して追加の認証方法をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="3de31-110">Custom authentication can be developed in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] to support additional authentication schemes.</span></span> <span data-ttu-id="3de31-111">そのためには、セキュリティ拡張機能インターフェイス <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension> を使用します。</span><span class="sxs-lookup"><span data-stu-id="3de31-111">This is made possible through the security extension interface <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension>.</span></span> <span data-ttu-id="3de31-112">レポート サーバーであらゆる拡張機能を配置および使用できるように、すべての拡張機能が <xref:Microsoft.ReportingServices.Interfaces.IExtension> ベース インターフェイスから継承されます。</span><span class="sxs-lookup"><span data-stu-id="3de31-112">All extensions inherit from the <xref:Microsoft.ReportingServices.Interfaces.IExtension> base interface for any extension deployed and used by the report server.</span></span> <span data-ttu-id="3de31-113"><xref:Microsoft.ReportingServices.Interfaces.IExtension> および <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension> は、<xref:Microsoft.ReportingServices.Interfaces> 名前空間のメンバーです。</span><span class="sxs-lookup"><span data-stu-id="3de31-113"><xref:Microsoft.ReportingServices.Interfaces.IExtension>, as well as <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension>, are members of the <xref:Microsoft.ReportingServices.Interfaces> namespace.</span></span>  
  
 <span data-ttu-id="3de31-114">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] では、レポート サーバーに対して認証を行うための主要な手段として、<xref:ReportService2010.ReportingService2010.LogonUser%2A> メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="3de31-114">The primary way to authenticate against a report server in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is the <xref:ReportService2010.ReportingService2010.LogonUser%2A> method.</span></span> <span data-ttu-id="3de31-115">Reporting Services Web サービスのこのメンバーを使用して、検証するユーザーの資格情報をレポート サーバーに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="3de31-115">This member of the Reporting Services Web service can be used to pass user credentials to a report server for validation.</span></span> <span data-ttu-id="3de31-116">基になるセキュリティ拡張機能によって、カスタム認証コードを含む**Iauthenticationextension**が実装されます。</span><span class="sxs-lookup"><span data-stu-id="3de31-116">Your underlying security extension implements **IAuthenticationExtension.LogonUser** which contains your custom authentication code.</span></span> <span data-ttu-id="3de31-117">フォーム認証のサンプルでは、**LogonUser** が指定された資格情報とデータベースのカスタム ユーザー ストアを比較する認証チェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="3de31-117">In the Forms Authentication sample, **LogonUser**, which performs an authentication check against the supplied credentials and a custom user store in a database.</span></span> <span data-ttu-id="3de31-118">**LogonUser** の実装例は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3de31-118">An example of an implementation of **LogonUser** looks like this:</span></span>  
  
```  
public bool LogonUser(string userName, string password, string authority)  
{  
   return AuthenticationUtilities.VerifyPassword(userName, password);  
}  
  
```  
  
 <span data-ttu-id="3de31-119">次のサンプル関数を使用して、指定された資格情報を検証します。</span><span class="sxs-lookup"><span data-stu-id="3de31-119">The following sample function is used to verify the supplied credentials:</span></span>  
  
```  
  
internal static bool VerifyPassword(string suppliedUserName,  
   string suppliedPassword)  
{   
   bool passwordMatch = false;  
   // Get the salt and pwd from the database based on the user name.  
   // See "How To: Use DPAPI (Machine Store) from ASP.NET," "How To:  
   // Use DPAPI (User Store) from Enterprise Services," and "How To:  
   // Create a DPAPI Library" for more information about how to use  
   // DPAPI to securely store connection strings.  
   SqlConnection conn = new SqlConnection(  
      "Server=localhost;" +   
      "Integrated Security=SSPI;" +  
      "database=UserAccounts");  
   SqlCommand cmd = new SqlCommand("LookupUser", conn);  
   cmd.CommandType = CommandType.StoredProcedure;  
  
   SqlParameter sqlParam = cmd.Parameters.Add("@userName",  
       SqlDbType.VarChar,  
       255);  
   sqlParam.Value = suppliedUserName;  
   try  
   {  
      conn.Open();  
      SqlDataReader reader = cmd.ExecuteReader();  
      reader.Read(); // Advance to the one and only row  
      // Return output parameters from returned data stream  
      string dbPasswordHash = reader.GetString(0);  
      string salt = reader.GetString(1);  
      reader.Close();  
      // Now take the salt and the password entered by the user  
      // and concatenate them together.  
      string passwordAndSalt = String.Concat(suppliedPassword, salt);  
      // Now hash them  
      string hashedPasswordAndSalt =  
         FormsAuthentication.HashPasswordForStoringInConfigFile(  
         passwordAndSalt,  
         "SHA1");  
      // Now verify them. Returns true if they are equal.  
      passwordMatch = hashedPasswordAndSalt.Equals(dbPasswordHash);  
   }  
   catch (Exception ex)  
   {  
       throw new Exception("Exception verifying password. " +  
          ex.Message);  
   }  
   finally  
   {  
       conn.Close();  
   }  
   return passwordMatch;  
}  
```  
  
## <a name="authentication-flow"></a><span data-ttu-id="3de31-120">認証フロー</span><span class="sxs-lookup"><span data-stu-id="3de31-120">Authentication Flow</span></span>  
 <span data-ttu-id="3de31-121">Reporting Services Web サービスには、レポート マネージャーとレポート サーバーによるフォーム認証を可能にするカスタム認証拡張機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="3de31-121">The Reporting Services Web service provides custom authentication extensions to enable Forms Authentication by Report Manager and the report server.</span></span>  
  
 <span data-ttu-id="3de31-122">Reporting Services Web サービスの <xref:ReportService2010.ReportingService2010.LogonUser%2A> メソッドを使用して、認証する資格情報をレポート サーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="3de31-122">The <xref:ReportService2010.ReportingService2010.LogonUser%2A> method of the Reporting Services Web service is used to submit credentials to the report server for authentication.</span></span> <span data-ttu-id="3de31-123">Web サービスは HTTP ヘッダーを使用して、検証されたログオン要求の認証チケット (クッキー) をサーバーからクライアントに渡します。</span><span class="sxs-lookup"><span data-stu-id="3de31-123">The Web service uses HTTP headers to pass an authentication ticket (known as a "cookie") from the server to the client for validated logon requests.</span></span>  
  
 <span data-ttu-id="3de31-124">次の図は、レポート サーバーがカスタム認証拡張機能を使用するように構成されたアプリケーション配置における、Web サービスのユーザーを認証するメソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="3de31-124">The following illustration depicts the method of authenticating users to the Web service when your application is deployed with a report server configured to use a custom authentication extension.</span></span>  
  
 <span data-ttu-id="3de31-125">![Reporting Services のセキュリティ認証フロー](../../media/rosettasecurityextensionauthenticationflow.gif "Reporting Services のセキュリティ認証フロー")</span><span class="sxs-lookup"><span data-stu-id="3de31-125">![Reporting Services security authentication flow](../../media/rosettasecurityextensionauthenticationflow.gif "Reporting Services security authentication flow")</span></span>  
  
 <span data-ttu-id="3de31-126">図 2 が示すように、認証プロセスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3de31-126">As shown in Figure 2, the authentication process is as follows:</span></span>  
  
1.  <span data-ttu-id="3de31-127">クライアント アプリケーションは、ユーザーを認証するために Web サービス メソッド <xref:ReportService2010.ReportingService2010.LogonUser%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3de31-127">A client application calls the Web service <xref:ReportService2010.ReportingService2010.LogonUser%2A> method to authenticate a user.</span></span>  
  
2.  <span data-ttu-id="3de31-128">Web サービスは、 <xref:ReportService2010.ReportingService2010.LogonUser%2A> セキュリティ拡張機能のメソッド (具体的には、 **iauthenticationextension**を実装するクラス) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3de31-128">The Web service makes a call to the <xref:ReportService2010.ReportingService2010.LogonUser%2A> method of your security extension, specifically, the class that implements **IAuthenticationExtension**.</span></span>  
  
3.  <span data-ttu-id="3de31-129"><xref:ReportService2010.ReportingService2010.LogonUser%2A> の実装によって、ユーザー ストアまたはセキュリティ機関のユーザー名とパスワードが検証されます。</span><span class="sxs-lookup"><span data-stu-id="3de31-129">Your implementation of <xref:ReportService2010.ReportingService2010.LogonUser%2A> validates the user name and password in the user store or security authority.</span></span>  
  
4.  <span data-ttu-id="3de31-130">認証の完了後に、Web サービスがクッキーを作成し、セッション用にそれを管理します。</span><span class="sxs-lookup"><span data-stu-id="3de31-130">Upon successful authentication, the Web service creates a cookie and manages it for the session.</span></span>  
  
5.  <span data-ttu-id="3de31-131">Web サービスは、HTTP ヘッダーの呼び出し元アプリケーションに認証チケットを返します。</span><span class="sxs-lookup"><span data-stu-id="3de31-131">The Web service returns the authentication ticket to the calling application on the HTTP header.</span></span>  
  
 <span data-ttu-id="3de31-132">Web サービスがセキュリティ拡張機能によってユーザーの認証を正常に完了すると、以降の要求に使用されるクッキーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="3de31-132">When the Web service successfully authenticates a user through the security extension, it generates a cookie that is used for subsequent requests.</span></span> <span data-ttu-id="3de31-133">クッキーをカスタム セキュリティ機関に保持することはできません。レポート サーバーがセキュリティ機関を所有していないためです。</span><span class="sxs-lookup"><span data-stu-id="3de31-133">The cookie may not persist within the custom security authority because the report server does not own the security authority.</span></span> <span data-ttu-id="3de31-134">クッキーは <xref:ReportService2010.ReportingService2010.LogonUser%2A> Web サービス メソッドから返され、以降の Web サービス メソッド呼び出しおよび URL アクセスに使用されます。</span><span class="sxs-lookup"><span data-stu-id="3de31-134">The cookie is returned from the <xref:ReportService2010.ReportingService2010.LogonUser%2A> Web service method and is used in subsequent Web service method calls and in URL access.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3de31-135">転送時にクッキーが損傷しないよう、<xref:ReportService2010.ReportingService2010.LogonUser%2A> から返される認証クッキーの転送を Secure Sockets Layer (SSL) 暗号化を使用して保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3de31-135">In order to avoid compromising the cookie during transmission, authentication cookies returned from <xref:ReportService2010.ReportingService2010.LogonUser%2A> should be transmitted securely using Secure Sockets Layer (SSL) encryption.</span></span>  
  
 <span data-ttu-id="3de31-136">カスタム セキュリティ拡張機能をインストールした場合に URL アクセスによってレポート サーバーにアクセスすると、インターネット インフォメーション サービス (IIS) および [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] が認証チケットの転送を自動的に管理します。</span><span class="sxs-lookup"><span data-stu-id="3de31-136">If you access the report server through URL access when a custom security extension is installed, Internet Information Services (IIS) and [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] automatically manage the transmission of the authentication ticket.</span></span> <span data-ttu-id="3de31-137">OAP API によってレポート サーバーにアクセスする場合は、プロキシ クラスの実装に認証チケット管理用の追加サポートを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="3de31-137">If you are accessing the report server through the SOAP API, your implementation of the proxy class must include additional support for managing the authentication ticket.</span></span> <span data-ttu-id="3de31-138">SOAP API の使用および認証チケットの管理の詳細については、「カスタム セキュリティでの Web サービスの使用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3de31-138">For more information about using the SOAP API and managing the authentication ticket, see "Using the Web Service with Custom Security."</span></span>  
  
## <a name="forms-authentication"></a><span data-ttu-id="3de31-139">フォーム認証</span><span class="sxs-lookup"><span data-stu-id="3de31-139">Forms Authentication</span></span>  
 <span data-ttu-id="3de31-140">フォーム認証は [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 認証の種類の 1 つであり、未認証ユーザーは HTML フォームにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="3de31-140">Forms Authentication is a type of [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] authentication in which an unauthenticated user is directed to an HTML form.</span></span> <span data-ttu-id="3de31-141">ユーザーが資格情報を入力すると、認証チケットを含むクッキーが発行されます。</span><span class="sxs-lookup"><span data-stu-id="3de31-141">Once the user provides credentials, the system issues a cookie containing an authentication ticket.</span></span> <span data-ttu-id="3de31-142">以降の要求では、クッキーをチェックしてユーザーがレポート サーバーによって認証されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="3de31-142">On later requests, the system first checks the cookie to see if the user was already authenticated by the report server.</span></span>  
  
 <span data-ttu-id="3de31-143">Reporting Services API から利用できるセキュリティ拡張機能インターフェイスを使用すると、フォーム認証をサポートするように [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="3de31-143">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] can be extended to support Forms Authentication using the security extensibility interfaces available through the Reporting Services API.</span></span> <span data-ttu-id="3de31-144">フォーム認証を使用するように [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] を拡張する場合は、レポート サーバーとのすべての通信に Secure Sockets Layer (SSL) を使用して、悪意のあるユーザーが別のユーザーのクッキーにアクセスすることを防止します。</span><span class="sxs-lookup"><span data-stu-id="3de31-144">If you extend [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] to use Forms Authentication, use Secure Sockets Layer (SSL) for all communications with the report server to prevent malicious users from gaining access to another user's cookie.</span></span> <span data-ttu-id="3de31-145">SSL を使用した場合、クライアントとレポート サーバーが相互に認証でき、2 台のコンピューター間の通信内容を他のコンピューターから読み取ることができなくなります。</span><span class="sxs-lookup"><span data-stu-id="3de31-145">SSL enables clients and a report server to authenticate each other and to ensure that no other computers can read the contents of communications between the two computers.</span></span> <span data-ttu-id="3de31-146">SSL 接続で送信されたすべてのデータが暗号化されるため、悪意のあるユーザーはレポート サーバーに送信されたパスワードやデータを傍受できません。</span><span class="sxs-lookup"><span data-stu-id="3de31-146">All data sent from a client through an SSL connection is encrypted so that malicious users cannot intercept passwords or data sent to a report server.</span></span>  
  
 <span data-ttu-id="3de31-147">一般に、フォーム認証は、Windows 以外のプラットフォームでのアカウントおよび認証をサポートするために実装されます。</span><span class="sxs-lookup"><span data-stu-id="3de31-147">Forms Authentication is generally implemented to support accounts and authentication for platforms other than Windows.</span></span> <span data-ttu-id="3de31-148">レポート サーバーへのアクセスを要求するユーザーにグラフィカル インターフェイスが表示され、入力した資格情報が認証のためにセキュリティ機関に送信されます。</span><span class="sxs-lookup"><span data-stu-id="3de31-148">A graphical interface is presented to a user who requests access to a report server, and the supplied credentials are submitted to a security authority for authentication.</span></span>  
  
 <span data-ttu-id="3de31-149">フォーム認証では、ユーザーが資格情報を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3de31-149">Forms Authentication requires that a person is present to enter credentials.</span></span> <span data-ttu-id="3de31-150">Reporting Services Web サービスと直接通信する自動アプリケーションの場合は、フォーム認証とカスタム認証方法を併用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3de31-150">For unattended applications that communicate directly with the Reporting Services Web service, Forms Authentication must be combined with a custom authentication scheme.</span></span>  
  
 <span data-ttu-id="3de31-151">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] でフォーム認証が適しているのは、次のような場合です。</span><span class="sxs-lookup"><span data-stu-id="3de31-151">Forms Authentication is appropriate for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] when:</span></span>  
  
-   <span data-ttu-id="3de31-152">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows アカウントを持たないユーザーを格納および認証する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="3de31-152">You need to store and authenticate users that do not have [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows accounts, and</span></span>  
  
-   <span data-ttu-id="3de31-153">Web サイトの異なるページ間で、ログオン ページとしてユーザー インターフェイス フォームを提供する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="3de31-153">You need to provide your own user interface form as a logon page between different pages on a Web site.</span></span>  
  
 <span data-ttu-id="3de31-154">フォーム認証をサポートするカスタム セキュリティ拡張機能を記述する場合は、次のことを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="3de31-154">Consider the following when writing a custom security extension that supports Forms Authentication:</span></span>  
  
-   <span data-ttu-id="3de31-155">フォーム認証を使用する場合は、インターネット インフォメーション サービス (IIS) のレポート サーバー仮想ディレクトリで匿名アクセスを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3de31-155">If you use Forms Authentication, anonymous access must be enabled on the report server virtual directory in Internet Information Services (IIS).</span></span>  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] <span data-ttu-id="3de31-156">認証を Forms に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3de31-156">authentication must be set to Forms.</span></span> <span data-ttu-id="3de31-157">レポート サーバーの Web.config ファイルで [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 認証を構成してください。</span><span class="sxs-lookup"><span data-stu-id="3de31-157">You configure [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] authentication in the Web.config file for the report server.</span></span>  
  
-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="3de31-158">では、Windows 認証またはカスタム認証を使用してユーザーを認証および承認できますが、両方を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="3de31-158">can authenticate and authorize users with either Windows Authentication or custom authentication, but not both.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="3de31-159">では、複数のセキュリティ拡張機能を同時に使用できません。</span><span class="sxs-lookup"><span data-stu-id="3de31-159">does not support simultaneous use of multiple security extensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3de31-160">参照</span><span class="sxs-lookup"><span data-stu-id="3de31-160">See Also</span></span>  
 [<span data-ttu-id="3de31-161">セキュリティ拡張機能の実装</span><span class="sxs-lookup"><span data-stu-id="3de31-161">Implementing a Security Extension</span></span>](../security-extension/implementing-a-security-extension.md)  
  
  
