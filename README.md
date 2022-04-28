**Notepad
using System;<br>
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
namespace WindowsFormsApp5
{
    public partial class Form1 : Form
    {
        private string fileName;
        private RichTextBox txtContent;
        private ToolBar toolBar;
        internal Form1()
        {
            fileName = null;
            initializeComponents();
        }
        void initializeComponents()
        {
            this.Text = "My notepad";
            this.MinimumSize = new Size(600, 450);
            this.FormClosing += new FormClosingEventHandler(NotepadClosing);
            this.MaximizeBox = true;<br>
            toolBar = new ToolBar();<br>
            toolBar.Font = new Font("Arial", 16);<br>
            toolBar.Padding = new Padding(4);<br>
            toolBar.ButtonClick += new ToolBarButtonClickEventHandler(toolBarClicked);<br>
            ToolBarButton toolBarButton1 = new ToolBarButton();<br>
            ToolBarButton toolBarButton2 = new ToolBarButton();<br>
            ToolBarButton toolBarButton3 = new ToolBarButton();<br>
            toolBarButton1.Text = "New";<br>
            toolBarButton2.Text = "Open";<br>
            toolBarButton3.Text = "Save";<br>
            toolBar.Buttons.Add(toolBarButton1);<br>
            toolBar.Buttons.Add(toolBarButton2);<br>
            toolBar.Buttons.Add(toolBarButton3);<br>
            txtContent = new RichTextBox();<br>
            txtContent.Size = this.ClientSize;<br>
            txtContent.Height -= toolBar.Height;<br>
            txtContent.Top = toolBar.Height;<br>
            txtContent.Anchor = AnchorStyles.Left | AnchorStyles.Right |<br>
           AnchorStyles.Top | AnchorStyles.Bottom;<br>
            txtContent.Font = new Font("Arial", 16);<br>
            txtContent.AcceptsTab = true;<br>
            txtContent.Padding = new Padding(8);<br>
this.Controls.Add(toolBar);<br>
            this.Controls.Add(txtContent);<br>
        }<br>
        private void toolBarClicked(Object sender, ToolBarButtonClickEventArgs e)<br>
        {<br>
            saveFile();<br>
            switch (toolBar.Buttons.IndexOf(e.Button))<br>
            {<br>
                case 0:<br>
                    this.Text += "My notepad";<br>
                    txtContent.Text = string.Empty;<br>
                    fileName = null<br>;
                    break;<br>
                case 1:<br>
                    OpenFileDialog openDlg = new OpenFileDialog();
                    if (DialogResult.OK == openDlg.ShowDialog())<br>
                    {<br>
                        fileName = openDlg.FileName;<br>
                        txtContent.LoadFile(fileName);<br>
                        this.Text = "My notepad " + fileName;<br>
                    }<br>
                  break;<br>                   
            }<br>
        }<br>
        void saveFile()<br>
        {
            if (fileName == null)<br>
            {<br>
                SaveFileDialog saveDlg = new SaveFileDialog();<br>
                if (DialogResult.OK == saveDlg.ShowDialog())<br>
                {<br>
                    fileName = saveDlg.FileName;<br>
                    this.Text += " " + fileName;<br>
                }<br>
            }<br>
            else<br>
            {<br>
                txtContent.SaveFile(fileName, RichTextBoxStreamType.RichText);<br>
            }<br>
        }<br>
        private void NotepadClosing(Object sender, FormClosingEventArgs e)<br>
        {<br>
            saveFile();<br>
        }<br>
        private void Form1_Load(object sender, EventArgs e)<br>
        {<br>
        }<br>
    }<br>
}<br>
**


**OUTPUT**

![image](https://user-images.githubusercontent.com/98301023/161000577-3679655f-ad3c-4f45-9fe6-53389b9fb952.png)




Convert Inr to usd and eur

using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace WindowsFormsApp3
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {
            {
                label4.Visible = true;
                if (textBox1.Text == "")
                {
                    label4.Text = "Enter the amount";
                }
                else
                {
                    Double convertedamt = Convert.ToDouble(textBox1.Text);
                    if (comboBox1.SelectedItem == "INR" && comboBox2.SelectedItem == "USD")
                    {
                        Double a = convertedamt / 74;
                        label4.Text = a + "$";
                    }
                    else if (comboBox1.SelectedItem == "INR" && comboBox2.SelectedItem == "SAR")
                    {
                        Double a = convertedamt / 17;
                        label4.Text = a + "SAR";
                    }
                    else if (comboBox1.SelectedItem == "INR" && comboBox2.SelectedItem == "EUR")
                    {

                        Double a = convertedamt / 11;
                        label4.Text = a + "EUR";
                    }
                    else
                    {
                        label4.Text = "Please Enter the conversion code";
                    }
                }
            }
        }

        private void button2_Click(object sender, EventArgs e)
        {
            textBox1.Text = "";
            label4.Text = "";
        }
    }
}

![image](https://user-images.githubusercontent.com/98301023/165699399-3b3df9e4-14e3-49e3-828d-c0bf62075634.png)

