<div align="center">

## Prevent more than one instance of any application


</div>

### Description

Purpose of this application is to have only one running instance of any c# application.

Uses "using System.Diagnostics" name space
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Nhilesh Baua](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/nhilesh-baua.md)
**Level**          |Intermediate
**User Rating**    |4.0 (8 globes from 2 users)
**Compatibility**  |C\#
**Category**       |[Coding Standards](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/coding-standards__10-33.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/nhilesh-baua-prevent-more-than-one-instance-of-any-application__10-4328/archive/master.zip)





### Source Code

<pre>
using System;
using System.Drawing;
using System.Collections;
using System.ComponentModel;
using System.Windows.Forms;
using System.Data;
using System.Reflection;
using DEAdmin.Classes;
using System.Diagnostics;
namespace DEAdmin
{
	<font color="green">
	/// <summary>
	/// Summary description for Form1.
	/// </summary></font>
	public class frmmain : System.Windows.Forms.Form
	{
		private System.ComponentModel.Container components = null;
		public frmmain()
		{
			<font color="green">	//
			// Required for Windows Form Designer support
			//	</font>
			InitializeComponent();
			<font color="green">	//
			// TODO: Add any constructor code after InitializeComponent call
			//	</font>
		}
 <font color="green">
		/// <summary>
		/// Clean up any resources being used.
		/// </summary>		 </font>
		protected override void Dispose( bool disposing )
		{
			if( disposing )
			{
				if (components != null)
				{
					components.Dispose();
				}
			}
			base.Dispose( disposing );
		}
		#region Windows Form Designer generated code
<font color="green">			/// <summary>
		/// Required method for Designer support - do not modify
		/// the contents of this method with the code editor.
		/// </summary>	</font>
		private void InitializeComponent()
		{
			<font color="green">	//
			// frmmain
			// </font>
			this.AutoScaleBaseSize = new System.Drawing.Size(5, 13);
			this.ClientSize = new System.Drawing.Size(792, 473);
			this.IsMdiContainer = true;
			this.Menu = this.mainMenu1;
			this.Name = "frmmain";
			this.StartPosition = System.Windows.Forms.FormStartPosition.CenterScreen;
			this.Text = "Dhalia Enterprise Main Screen";
			this.WindowState = System.Windows.Forms.FormWindowState.Maximized;
			this.Resize += new System.EventHandler(this.frmmain_Resize);
			this.Load += new System.EventHandler(this.Form1_Load);
		}
		#endregion
<font color="green">		/// <summary>
		/// The main entry point for the application.
		/// </summary></font>
		[STAThread]
		static void Main()
		{
			Application.Run(new frmmain());
		}
		private void dataGrid1_Navigate(object sender, System.Windows.Forms.NavigateEventArgs ne)
		{
		}
		private void Form1_Load(object sender, System.EventArgs e)
		{
			if (RunningInstance()!=null)
			{
				this.Dispose();
			}
		}
		public static Process RunningInstance()
		{
			Process current = Process.GetCurrentProcess();
			Process[] processes = Process.GetProcessesByName (current.ProcessName);
			<font color="green">//Loop through the running processes in with the same name </font>
			foreach (Process process in processes)
			{
				if (process.Id != current.Id)
				{
					if (Assembly.GetExecutingAssembly().Location.Replace("/", "\\") == current.MainModule.FileName)
					{
						return process;
					}
				}
			}
			return null;
		}
		</pre>

