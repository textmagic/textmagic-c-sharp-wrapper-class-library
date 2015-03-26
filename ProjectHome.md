## Since Google has been discounted **Downloads** feature at Google Code, we moved Downloads section <a href='https://drive.google.com/folderview?id=0B1j_HRAua5sxQktzR0U1amNqZk0&usp=sharing'>here</a>. ##

How to use .NET for TextMagic API:

  1. Register on TextMagic: https://www.textmagic.com/
  1. Download TextMagic C# Wrapper [class library package](https://drive.google.com/folderview?id=0B1j_HRAua5sxQktzR0U1amNqZk0&usp=sharing) and reference `TextMagicServices.dll` to your project. In _Visual Studio_, you should go to **`Project - Add Reference`** window and locate dll by clicking **`Browse`** button. In _SharpDevelop_, go to **`Project - Add Reference - .NET Assembly Browser`** and choose dll by clicking **`Browse`** button. That's it! Now you can use `TextMagicServices` class as described below.
  1. Write Code like:

```

using System;
using System.Collections.Generic;

namespace textmagicsample
{
	class Program
	{
		public static void Main(string[] args)
		{
			TextMagicServices.TextMagicMessageService TMS;
			
			string username  = "useraccount";
			string password  = "GFge3M7yV0UMOuI";			
			string text      = "Test";
			string phone     = "999123456";
			long   messageId = 104424;
			
			Console.WriteLine("Connecting to TextMagic");
			TMS = new TextMagicServices.TextMagicMessageService(username, password);
			
			Console.WriteLine("Sending message to a single phone");
			TextMagicServices.SentMessage sentMessage = new TextMagicServices.SentMessage();
			sentMessage = TMS.send(text, phone);
			
			Console.WriteLine("Sending message to multiple phones");
			List<string> phonesList = new List<string>();
			phonesList.Add("999123456");
			phonesList.Add("999223456");
			phonesList.Add("999323456");
			List<TextMagicServices.SentMessage> sentMessages = new List<TextMagicServices.SentMessage>();
			sentMessages = TMS.send(text, phonesList);
			
			Console.WriteLine("Checking balance: " + TMS.account());
			
			Console.WriteLine("Checking message " + messageId.ToString() + " status");
			TextMagicServices.MessageStatus messageStatus;
			messageStatus = TMS.messageStatus(messageId);
			
			Console.WriteLine("Checking message multiple message statuses");
			List<long> messageIds = new List<long>();

                        messageIds.Add(8776337);
                        messageIds.Add(8776338);

                        List<TextMagicServices.MessageStatus> messageStatuses;

                        messageStatuses = TMS.messageStatus(messageIds);
			
			Console.Write("Press any key to continue . . . ");
			Console.ReadKey(true);
		}
	}
}

```

4. So simple... :)

**Please note:** in case you want to rebuild `TextMagicService.dll` from source, you should add reference to `Newtonsoft.Json` library just by adding dll included in the source archive (`\bin\Debug\Newtonsoft.Json.dll`) because of possible version conflict.

# <a href='http://www.textmagic.com/affiliate/fordevelopers.html'>SMS Gateway Affiliate Programme For Developers</a> #

Here’s what you’ll get:

<li>A 10% share of the lifetime value of the customer. If a customer spends £5,000 on SMS credit during his or her membership of TextMagic, you’ll earn £500.</li>

<li>Bonus: we’ll pay you a £15 flat fee for each new paying customer referral. You’ll still get your 10% revenue share from their initial order, too.</li>