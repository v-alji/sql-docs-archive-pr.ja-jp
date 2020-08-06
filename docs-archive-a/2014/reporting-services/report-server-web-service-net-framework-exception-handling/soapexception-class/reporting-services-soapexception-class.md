---
title: Reporting Services SoapException クラス | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], SoapException class
- SoapException class
ms.assetid: 2cec49ee-20b1-40eb-a75b-0908d9c05b34
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f6efdfac89014116957990ef2db21cf52e76a4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715094"
---
# <a name="reporting-services-soapexception-class"></a><span data-ttu-id="d3f84-102">Reporting Services SoapException クラス</span><span class="sxs-lookup"><span data-stu-id="d3f84-102">Reporting Services SoapException Class</span></span>
  <span data-ttu-id="d3f84-103">発生が予想される [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のエラーには、対処が必要です。</span><span class="sxs-lookup"><span data-stu-id="d3f84-103">You should address specific [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] errors that you know might happen.</span></span> <span data-ttu-id="d3f84-104">たとえば、ユーザーにフォルダーの作成を要求するアプリケーションでは、ユーザーが既に存在するフォルダーを作成する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d3f84-104">For example, in an application where you ask the user to create a folder, it might be possible for the user to try to create a folder that already exists.</span></span> <span data-ttu-id="d3f84-105">開発者としては、アプリケーションのフォルダー名フィールドとパス フィールドにユーザーが入力する内容を制限することはできません。ただし、既に存在するアイテムをユーザーが誤って作成しようとしたとき、どのように対処するかを指定することは可能です。</span><span class="sxs-lookup"><span data-stu-id="d3f84-105">As the developer, you do not have control over what the user enters in the folder name and path fields of your application, but you do have control over what the user experience is when someone incidentally tries to create an item that already exists.</span></span>  
  
 <span data-ttu-id="d3f84-106">エラー状態を容易に検出できるようにするため、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] は例外のエラー コードを分類し、**SoapException** クラスのプロパティを使用してエラーの分類を返します。</span><span class="sxs-lookup"><span data-stu-id="d3f84-106">To make it easier for you to catch specific error conditions, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] classifies an error code for the exception and returns the classification of the error using properties from the **SoapException** class.</span></span> <span data-ttu-id="d3f84-107">詳細については、SDK ドキュメントの「SoapException クラス」を参照してください [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d3f84-107">For more information, see "SoapException Class" in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
 <span data-ttu-id="d3f84-108">次の表は、**SoapException** クラスのパブリック プロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="d3f84-108">The following table lists the public properties of the **SoapException** class.</span></span>  
  
|<span data-ttu-id="d3f84-109">パブリック プロパティ</span><span class="sxs-lookup"><span data-stu-id="d3f84-109">Public property</span></span>|<span data-ttu-id="d3f84-110">説明</span><span class="sxs-lookup"><span data-stu-id="d3f84-110">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="d3f84-111">**俳優**</span><span class="sxs-lookup"><span data-stu-id="d3f84-111">**Actor**</span></span>|<span data-ttu-id="d3f84-112">例外の原因となったコード。</span><span class="sxs-lookup"><span data-stu-id="d3f84-112">The code that caused the exception.</span></span> <span data-ttu-id="d3f84-113">値は Web サービス メソッドへの URL です。</span><span class="sxs-lookup"><span data-stu-id="d3f84-113">The value is the URL to the Web service method.</span></span>|  
|<span data-ttu-id="d3f84-114">**詳細**</span><span class="sxs-lookup"><span data-stu-id="d3f84-114">**Detail**</span></span>|<span data-ttu-id="d3f84-115">アプリケーション固有のエラー情報。</span><span class="sxs-lookup"><span data-stu-id="d3f84-115">Application-specific error information.</span></span> <span data-ttu-id="d3f84-116">この値は、レポート サーバーによって XML 形式で設定されます。</span><span class="sxs-lookup"><span data-stu-id="d3f84-116">The value is set by the report server and is in XML format.</span></span> <span data-ttu-id="d3f84-117">詳細については、「[Detail プロパティ](detail-property.md)」と「[Detail プロパティを使用したエラー処理](../best-practices/using-the-detail-property-to-handle-specific-errors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3f84-117">For more information, see [Detail Property](detail-property.md) and [Using the Detail Property to Handle Specific Errors](../best-practices/using-the-detail-property-to-handle-specific-errors.md).</span></span>|  
|<span data-ttu-id="d3f84-118">**HelpLink**</span><span class="sxs-lookup"><span data-stu-id="d3f84-118">**HelpLink**</span></span>|<span data-ttu-id="d3f84-119">エラーに関連付けられたヘルプ ファイルへの URL または URN。</span><span class="sxs-lookup"><span data-stu-id="d3f84-119">A URL or URN to a Help file associated with the error.</span></span> <span data-ttu-id="d3f84-120">通常、この値は、Web サービスによって [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ヘルプとサポート サイトの URL に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d3f84-120">The value is usually set by the Web service and it sets a URL to [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Help and Support.</span></span> <span data-ttu-id="d3f84-121">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] では発生するエラーのヘルプ リンクが複数サポートされているので、レポート サーバーは、**Detail** プロパティの一部としてヘルプ リンク情報を設定します。</span><span class="sxs-lookup"><span data-stu-id="d3f84-121">Because [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] supports multiple help links for errors that occur, the report server sets help link information as part of the **Detail** property.</span></span> <span data-ttu-id="d3f84-122">詳細については、「[HelpLink 要素](helplink-element.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3f84-122">For more information, see [HelpLink Element](helplink-element.md).</span></span>|  
|<span data-ttu-id="d3f84-123">**Message**</span><span class="sxs-lookup"><span data-stu-id="d3f84-123">**Message**</span></span>|<span data-ttu-id="d3f84-124">エラーを説明するローカライズされたメッセージ。</span><span class="sxs-lookup"><span data-stu-id="d3f84-124">A descriptive, localized message that describes the error.</span></span> <span data-ttu-id="d3f84-125">このテキストはアプリケーションの UI に表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="d3f84-125">This text might appear in the application UI.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3f84-126">参照</span><span class="sxs-lookup"><span data-stu-id="d3f84-126">See Also</span></span>  
 <span data-ttu-id="d3f84-127">[Reporting Services における例外処理の概要](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="d3f84-127">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="d3f84-128">SoapException エラー テーブル</span><span class="sxs-lookup"><span data-stu-id="d3f84-128">SoapException Errors Table</span></span>](soapexception-errors-table.md)  
  
  
