---
title: Web サービス認証 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], authentication
- XML Web service [Reporting Services], authentication
- Report Server Web service, authentication
ms.assetid: 852b4947-a090-4e54-8555-5a503945ceab
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0c7836d6eba8c6ab3f0a8e705ebb79c7ed73eb17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739204"
---
# <a name="web-service-authentication"></a><span data-ttu-id="e8067-102">Web サービス認証</span><span class="sxs-lookup"><span data-stu-id="e8067-102">Web Service Authentication</span></span>
  <span data-ttu-id="e8067-103">Windows 認証または基本認証を使用して、レポート サーバー Web サービスへの呼び出しを認証できます。</span><span class="sxs-lookup"><span data-stu-id="e8067-103">You can use either Windows Authentication or Basic authentication to authenticate the calls made to the Report Server Web service.</span></span> <span data-ttu-id="e8067-104">レポート サーバーへの SOAP 要求を作成するクライアントは、サポートされる認証プロトコルのいずれかのクライアント部分を実装している必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8067-104">Any client that makes SOAP requests to the report server must implement the client portion of one of the supported authentication protocols.</span></span> <span data-ttu-id="e8067-105">を使用している場合は、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] マネージコード HTTP クラスを使用して認証を実装できます。</span><span class="sxs-lookup"><span data-stu-id="e8067-105">If you are using the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], you can use the managed code HTTP classes to implement authentication.</span></span> <span data-ttu-id="e8067-106">これらの API を使用すると、認証情報を SOAP 要求と一緒に容易に送信できます。</span><span class="sxs-lookup"><span data-stu-id="e8067-106">Using these APIs makes it easy to send authentication information along with the SOAP requests.</span></span>  
  
 <span data-ttu-id="e8067-107">レポート サーバー Web サービスへの呼び出しを作成する前に適切な資格情報を持っていないと、呼び出しが失敗します。</span><span class="sxs-lookup"><span data-stu-id="e8067-107">If you do not have appropriate credentials before you make a call to the Report Server Web service, the call fails.</span></span> <span data-ttu-id="e8067-108">実行時に、メソッドを呼び出す前の Web サービスを表すクライアント側オブジェクトの **Credentials** プロパティを設定することによって、資格情報を Web サービスに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="e8067-108">At run time, you can pass credentials to the Web service by setting the **Credentials** property of the client-side object that represents the Web service before you call its methods.</span></span>  
  
 <span data-ttu-id="e8067-109">以降のセクションでは、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] を使用して資格情報を送信するコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="e8067-109">The following sections contain example code that sends credentials using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="windows-authentication"></a><span data-ttu-id="e8067-110">Windows 認証</span><span class="sxs-lookup"><span data-stu-id="e8067-110">Windows Authentication</span></span>  
 <span data-ttu-id="e8067-111">次のコードは、Windows 資格情報を Web サービスに渡します。</span><span class="sxs-lookup"><span data-stu-id="e8067-111">The following code passes Windows credentials to the Web service.</span></span>  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
ReportingService rs = new ReportingService();  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
```  
  
## <a name="basic-authentication"></a><span data-ttu-id="e8067-112">基本認証</span><span class="sxs-lookup"><span data-stu-id="e8067-112">Basic Authentication</span></span>  
 <span data-ttu-id="e8067-113">次のコードは、基本資格情報を Web サービスに渡します。</span><span class="sxs-lookup"><span data-stu-id="e8067-113">The following code passes Basic credentials to the Web service.</span></span>  
  
```vb  
Dim rs As New ReportingService()  
rs.Credentials = New System.Net.NetworkCredential("username", "password", "domain")  
```  
  
```csharp  
ReportingService service = new ReportingService();  
service.Credentials = new System.Net.NetworkCredential("username", "password", "domain");  
```  
  
 <span data-ttu-id="e8067-114">資格情報は、レポート サーバー Web サービスのメソッドを呼び出す前に設定しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8067-114">The credentials must be set before you call any of the methods of the Report Server Web service.</span></span> <span data-ttu-id="e8067-115">資格情報を設定しないと、"HTTP 401 エラー : アクセスが拒否されました。" というエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e8067-115">If you do not set the credentials, you receive the error code an HTTP 401 Error: Access Denied.</span></span> <span data-ttu-id="e8067-116">サービスを使う前にサービスを認証する必要があります。ただし、資格情報を設定した後は、*rs* などの同じサービス変数を続けて使う限り、再度設定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e8067-116">You must authenticate the service before you use it, but after you have set the credentials, you do not need to set them again as long as you continue to use the same service variable (such as *rs*).</span></span>  
  
## <a name="custom-authentication"></a><span data-ttu-id="e8067-117">カスタム認証</span><span class="sxs-lookup"><span data-stu-id="e8067-117">Custom Authentication</span></span>  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="e8067-118">にはプログラミング API が含まれ、開発者は、セキュリティ拡張機能と呼ばれるカスタム認証拡張機能を設計および開発できます。</span><span class="sxs-lookup"><span data-stu-id="e8067-118">includes a programming API that provides developers with the opportunity to design and develop custom authentication extensions, known as security extensions.</span></span> <span data-ttu-id="e8067-119">詳細については、「 [Implementing a Security Extension](../../extensions/security-extension/implementing-a-security-extension.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8067-119">For more information, see [Implementing a Security Extension](../../extensions/security-extension/implementing-a-security-extension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8067-120">参照</span><span class="sxs-lookup"><span data-stu-id="e8067-120">See Also</span></span>  
 <span data-ttu-id="e8067-121">[Web サービスと .NET Framework を使用してのアプリケーションの構築](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="e8067-121">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="e8067-122">レポート サーバー web サービス</span><span class="sxs-lookup"><span data-stu-id="e8067-122">Report Server Web Service</span></span>](../report-server-web-service.md)  
  
  
