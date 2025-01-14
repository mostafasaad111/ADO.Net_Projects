# ADO.Net_Projects

## Pizza project 
              using System;
              using System.Windows.Forms;
              
              namespace WindowsFormsApp3
              {
                  public partial class PizzaOrder : Form
                  {
                      public PizzaOrder()
                      {
                          InitializeComponent();
                      }
              
                      private void rbSmall_CheckedChanged(object sender, EventArgs e)
                      {
                          lbSize.Text = rbSmall.Checked ? rbSmall.Text : string.Empty;
                          UpdatePrice();
                      }
              
                      private void rbMedium_CheckedChanged(object sender, EventArgs e)
                      {
                          lbSize.Text = rbMedium.Checked ? rbMedium.Text : string.Empty;
                          UpdatePrice();
              
                      }
              
                      private void rbLarge_CheckedChanged(object sender, EventArgs e)
                      {
                          lbSize.Text = rbLarge.Checked ? rbLarge.Text : string.Empty;
                          UpdatePrice();
              
                      }
              
                      //start chekced Box //
              
                      void UpdateTappings()
                      {
              
                          string sTapping = "";
              
                          if (chExtraChees.Checked)
                          {
                              sTapping = " ExtraChees";
                          }
                          if (chOlives.Checked)
                          {
                              sTapping += ", Olives";
                          }
                          if (chOnion.Checked)
                          {
                              sTapping += ",Onion";
                          }
                          if (chTomatoes.Checked)
                          {
                              sTapping += ", Tomatoes";
                          }
                          if (chMushrooms.Checked)
                          {
                              sTapping += ", Mushrooms";
                          }
                          if (chGreenPeppers.Checked)
                          {
                              sTapping += ", GreenPeppers";
                          }
                          if (sTapping.StartsWith(","))
                          {
                              sTapping = sTapping.Substring(1, sTapping.Length - 1).Trim();
                          }
                          if (sTapping == "")
                              sTapping = "No Tappings";
              
                          lbToppings.Text = sTapping;
              
                      }
              
                      float CountTopping()
                      {
                          float TotalTappingPrice = 0;
                          if (chMushrooms.Checked)
                          {
                              TotalTappingPrice += Convert.ToSingle(chMushrooms.Tag);
                          }
                          if (chExtraChees.Checked)
                          {
                              TotalTappingPrice += Convert.ToSingle(chExtraChees.Tag);
                          }
                          if (chGreenPeppers.Checked)
                          {
                              TotalTappingPrice += Convert.ToSingle(chGreenPeppers.Tag);
                          }
                          if (chTomatoes.Checked)
                          {
                              TotalTappingPrice += Convert.ToSingle(chTomatoes.Tag);
                          }
                          if (chOnion.Checked)
                          {
                              TotalTappingPrice += Convert.ToSingle(chOnion.Tag);
                          }
                          if (chOlives.Checked)
                          {
                              TotalTappingPrice += Convert.ToSingle(chOlives.Tag);
                          }
                          return TotalTappingPrice;
                      }
                      float CountSize()
                      {
                          if (rbSmall.Checked)
                          {
                              return Convert.ToSingle(rbSmall.Tag);
                          }
                          else if (rbMedium.Checked)
                          {
                              return Convert.ToSingle(rbMedium.Tag);
                          }
                          else
                          {
                              return Convert.ToSingle(rbLarge.Tag);
                          }
              
                      }
                      float CountCrsutType()
                      {
                          return rbThick.Checked ? Convert.ToSingle(rbThick.Tag) : Convert.ToSingle(rbThin.Tag);
                      }
                      void UpdatePrice()
                      {
                          float Totla = CountTopping() + CountCrsutType() + CountSize();
                          lbPrice.Text = $"${Totla}";
                      }
              
                      private void checkBox6_CheckedChanged(object sender, EventArgs e)
                      {
                          UpdateTappings();
                          UpdatePrice();
                      }
                      private void chMushrooms_CheckedChanged(object sender, EventArgs e)
                      {
                          UpdateTappings();
                          UpdatePrice();
                      }
              
                      private void chTomatoes_CheckedChanged(object sender, EventArgs e)
                      {
                          UpdateTappings();
                          UpdatePrice();
                      }
              
                      private void chOnion_CheckedChanged(object sender, EventArgs e)
                      {
                          UpdateTappings();
                          UpdatePrice();
                      }
              
                      private void chOlives_CheckedChanged(object sender, EventArgs e)
                      {
                          UpdateTappings();
                          UpdatePrice();
                      }
              
                      private void chGreenPeppers_CheckedChanged(object sender, EventArgs e)
                      {
                          UpdateTappings();
                          UpdatePrice();
                      }
              
                      // End Checked Box // 
              
                      // Start Crust
                      private void rbThin_CheckedChanged(object sender, EventArgs e)
                      {
                          lbCrustType.Text = rbThin.Checked ? rbThin.Text : string.Empty;
                          UpdatePrice();
                      }
              
                      private void rbThick_CheckedChanged(object sender, EventArgs e)
                      {
                          lbCrustType.Text = rbThick.Checked ? rbThick.Text : string.Empty;
                          UpdatePrice();
                      }
              
                      //start Eat 
                      private void rbEatIn_CheckedChanged(object sender, EventArgs e)
                      {
                          lbEat.Text = rbEatIn.Checked ? rbEatIn.Text : string.Empty;
                      }
              
                      private void rbEatOut_CheckedChanged(object sender, EventArgs e)
                      {
                          lbEat.Text = rbEatOut.Checked ? rbEatOut.Text : string.Empty;
              
                      }
              
                      private void lbPrice_Click(object sender, EventArgs e)
                      {
                          lbPrice.Text = Convert.ToString(CountCrsutType() + CountSize() + CountTopping());
                      }
              
                      private void button1_Click(object sender, EventArgs e)
                      {
                          if (MessageBox.Show("Confirm Order", "Confirm", MessageBoxButtons.OKCancel, MessageBoxIcon.Question) == DialogResult.OK)
                          {
                              if (MessageBox.Show("Order Placed Successfuly", "Success", MessageBoxButtons.OK, MessageBoxIcon.Information) == DialogResult.OK)
                              {
                                  gbSize.Enabled = false;
                                  gbEat.Enabled = false;
                                  gbCrust.Enabled = false;
                                  gbTopping.Enabled = false;
                                  btOrderPiza.Enabled = false;
                              }
                          }
                      }
              
                      private void groupBox2_Enter(object sender, EventArgs e)
                      {
              
                      }
              
                      private void button2_Click(object sender, EventArgs e)
                      {
                          gbSize.Enabled = true;
                          gbEat.Enabled = true;
                          gbCrust.Enabled = true;
                          gbTopping.Enabled = true;
                      }

                      private void PizzaOrder_Load(object sender, EventArgs e)
                      {
              
                      }
                  }
              }

## PictureBox Project 1 

                      using System;
                      using System.Drawing;
                      using System.Windows.Forms;
                      using WindowsFormsApp4.Properties;
                      
                      namespace WindowsFormsApp4
                      {
                          public partial class Form1 : Form
                          {
                              public Form1()
                              {
                                  InitializeComponent();
                              }
                      
                              private void textBox5_TextChanged(object sender, EventArgs e)
                              {
                      
                              }
                      
                      
                      
                              private void pictureBox1_Click(object sender, EventArgs e)
                              {
                      
                              }
                      
                              private void DeskTop_Click(object sender, EventArgs e)
                              {
                                  pictureBox1.Image = Resources.g6;
                      
                              }
                      
                              private void Book_Click(object sender, EventArgs e)
                              {
                                  pictureBox1.Image = Resources.g5;
                              }
                      
                              private void LoadPicture_Click(object sender, EventArgs e)
                              {
                                  pictureBox1.Image = Image.FromFile(@"C:\Users\AAA\Desktop\photo\g1.jpg");
                              }
                          }
                      }

##   PictureBox Project 2   

                  using PictureBox.Properties;
                  using System;
                  using System.Drawing;
                  using System.Windows.Forms;
                  
                  namespace PictureBox
                  {
                      public partial class Form1 : Form
                      {
                          public Form1()
                          {
                              InitializeComponent();
                          }
                  
                          private void rbBoy_CheckedChanged(object sender, EventArgs e)
                          {
                              label1.Text = rbBoy.Checked ? rbBoy.Text : string.Empty;
                              pictureBox1.Image = Resources.boy;
                          }
                  
                          private void rbGirl_CheckedChanged(object sender, EventArgs e)
                          {
                              label1.Text = rbGirl.Checked ? rbGirl.Text : string.Empty;
                              pictureBox1.Image = Resources.Girl;
                          }
                  
                          private void rbPen_CheckedChanged(object sender, EventArgs e)
                          {
                              label1.Text = ((RadioButton)sender).Tag.ToString();
                              pictureBox1.Image = Image.FromFile(@"C:\Users\AAA\Desktop\photo\Pen.png");
                          }
                  
                          private void rbBook_CheckedChanged(object sender, EventArgs e)
                          {
                              label1.Text = ((RadioButton)sender).Tag.ToString();
                              pictureBox1.Image = Image.FromFile(@"C:\Users\AAA\Desktop\photo\g5.png");
                          }
                      }
                  }

## Draw Line 

                using System.Drawing;
                using System.Windows.Forms;
                
                namespace WindowsFormsApp5
                {
                    public partial class Form1 : Form
                    {
                        public Form1()
                        {
                            InitializeComponent();
                        }
                
                        private void Form1_Paint(object sender, PaintEventArgs e)
                        {
                            Color Black = Color.FromArgb(255, 0, 0, 0);
                            Pen Pen = new Pen(Black);
                            Pen.Width = 10;
                r
                            //  Pen.DashCap = System.Drawing.Drawing2D.DashStyle.Dash ;
                            Pen.StartCap = System.Drawing.Drawing2D.LineCap.Round;
                            Pen.EndCap = System.Drawing.Drawing2D.LineCap.Round;
                
                            e.Graphics.DrawLine(Pen, 100, 100, 100, 200);
                            e.Graphics.DrawRectangle(Pen, 200, 200, 300, 300);
                            e.Graphics.DrawEllipse(Pen, 200, 50, 100, 120);
                        }
                    }
                }

## Tic Tac Toe Game 

                      using System;
                      using System.Collections.Generic;
                      using System.ComponentModel;
                      using System.Data;
                      using System.Drawing;
                      using System.IO;
                      using System.Linq;
                      using System.Runtime.InteropServices.WindowsRuntime;
                      using System.Text;
                      using System.Threading.Tasks;
                      using System.Windows.Forms;
                      using System.Xml.Linq;
                      using XO_Game_Final.Properties;
                      
                      namespace XO_Game_Final
                      {
                          public partial class Form1 : Form
                          {
                      
                              stGameStatus GameStatus;
                              enPlayer PlayerTurn = enPlayer.Player1;
                              enum enPlayer
                              {
                                  Player1,
                                  Player2
                              }
                      
                              enum enWinner
                              {
                                  Player1,
                                  Player2,
                                  Draw,
                                  GameInProgress
                              }
                      
                              struct stGameStatus
                              {
                                  public enWinner Winner;
                                  public bool GameOver;
                                  public short PlayCount;
                      
                              }
                      
                      
                            
                              public bool CheckValues(Button btn1, Button btn2, Button btn3)
                              {
                                 
                      
                                  if (btn1.Tag.ToString() != "?" && btn1.Tag.ToString() == btn2.Tag.ToString() && btn1.Tag.ToString() == btn3.Tag.ToString())
                                  {
                      
                                      btn1.BackColor = Color.GreenYellow;
                                      btn2.BackColor = Color.GreenYellow;
                                      btn3.BackColor = Color.GreenYellow;
                      
                                      if (btn1.Tag.ToString() == "X")
                                      {
                                          GameStatus.Winner = enWinner.Player1;
                                          GameStatus.GameOver = true;
                                          EndGame();
                                          return true;
                                      }
                                      else
                                      {
                                          GameStatus.Winner = enWinner.Player2;
                                          GameStatus.GameOver = true;
                                          EndGame();
                                          return true;
                                      }
                      
                                  }
                                  
                                  GameStatus.GameOver = false;
                                  return false;
                      
                      
                              }
                      
                              void EndGame()
                              {
                      
                                  lblTurn.Text = "Game Over";
                                  switch (GameStatus.Winner)
                                  {
                                       
                                      case enWinner.Player1:
                                         
                                             lblWinner.Text = "Player1";
                                              break;
                                         
                                      case enWinner.Player2:
                                         
                                              lblWinner.Text = "Player2";
                                              break;
                      
                                      default:
                      
                                              lblWinner.Text = "Draw";
                                              break;
                      
                                  }
                      
                                  MessageBox.Show("GameOver", "GameOver", MessageBoxButtons.OK, MessageBoxIcon.Information);
                      
                              }
                      
                              public void  CheckWinner()
                              {
                      
                            
                                  //checked rows
                                  //check Row1
                                  if (CheckValues(button1, button2, button3))
                                   return;
                      
                                  //check Row2
                                  if (CheckValues(button4, button5, button6))
                                      return;
                      
                                  //check Row3
                                  if (CheckValues(button7, button8, button9))
                                      return;
                      
                                  //checked cols
                                  //check col1
                                  if (CheckValues(button1, button4, button7))
                                      return;
                      
                                  //check col2
                                  if (CheckValues(button2, button5, button8))
                                      return;
                      
                                  //check col3
                                  if (CheckValues(button3, button6, button9))
                                      return;
                      
                                  //check Diagonal
                      
                                  //check Diagonal1
                                  if (CheckValues(button1, button5, button9))
                                      return;
                      
                                  //check Diagonal2
                                  if (CheckValues(button3, button5, button7))
                                      return;
                      
                      
                              }
                      
                      
                              public void ChangeImage(Button btn)
                              {
                      
                                  if (btn.Tag.ToString()=="?")
                                  {
                                      switch (PlayerTurn)
                                      {
                                          case enPlayer.Player1:
                                              btn.Image = Resources.X;
                                              PlayerTurn= enPlayer.Player2;
                                              lblTurn.Text = "Player 2";
                                              GameStatus.PlayCount++;
                                              btn.Tag = "X";
                                              CheckWinner();
                                              break;
                                          case enPlayer.Player2:
                                              btn.Image = Resources.O;
                                              PlayerTurn = enPlayer.Player1;
                                              lblTurn.Text = "Player 1";
                                              GameStatus.PlayCount++;
                                              btn.Tag = "O";
                                              CheckWinner();
                                              break;
                                      }
                                  }
                                  
                                  else
                      
                                  {
                                      MessageBox.Show("Wrong Choice","Worng",MessageBoxButtons.OK,MessageBoxIcon.Error);
                                  }
                      
                                  if(GameStatus.PlayCount ==9)
                                  {
                                      GameStatus.GameOver = true;
                                      GameStatus.Winner = enWinner.Draw;
                                      EndGame();
                                  }
                                 
                                
                              }
                      
                              public Form1()
                              {
                                  InitializeComponent();
                              }
                      
                              private void button1_Click(object sender, EventArgs e)
                              {
                                  ChangeImage(button1);
                              }
                      
                              private void button2_Click(object sender, EventArgs e)
                              {
                                  ChangeImage(button2);
                              }
                      
                              private void button3_Click(object sender, EventArgs e)
                              {
                                  ChangeImage(button3);
                              }
                      
                              private void button6_Click(object sender, EventArgs e)
                              {
                                  ChangeImage(button6);
                              }
                      
                              private void button5_Click(object sender, EventArgs e)
                              {
                                  ChangeImage(button5);
                              }
                      
                              private void button4_Click(object sender, EventArgs e)
                              {
                                  ChangeImage(button4);
                              }
                      
                              private void button9_Click(object sender, EventArgs e)
                              {
                                  ChangeImage(button9);
                              }
                      
                              private void button8_Click(object sender, EventArgs e)
                              {
                                  ChangeImage(button8);
                              }
                      
                              private void button7_Click(object sender, EventArgs e)
                              {
                                  ChangeImage(button7);
                              }
                      
                              private void Form1_Load(object sender, EventArgs e)
                              {
                      
                              }
                      
                              private void RestButton(Button btn)
                              {
                                  btn.Image = Resources.question_mark_96;
                                  btn.Tag = "?";
                                  btn.BackColor = Color.Transparent;
                                  
                              }
                              private void RestartGame()
                              {
                      
                                  RestButton(button1);
                                  RestButton(button2);
                                  RestButton(button3);
                                  RestButton(button4);
                                  RestButton(button5);
                                  RestButton(button6);
                                  RestButton(button7);
                                  RestButton(button8);
                                  RestButton(button9);
                      
                                  PlayerTurn = enPlayer.Player1;
                                  lblTurn.Text = "Player 1";
                                  GameStatus.PlayCount =0;
                                  GameStatus.GameOver = false;
                                  GameStatus.Winner = enWinner.GameInProgress;
                                  lblWinner.Text = "In Progress";
                      
                      
                      
                              }
                              private void btnRestart_Click(object sender, EventArgs e)
                              {
                                  RestartGame();
                      
                              }
                      
                             
                              private void Form1_Paint(object sender, PaintEventArgs e)
                              {
                      
                                  Color white = Color.FromArgb(255, 255, 255,255);
                                  Pen whitePen = new Pen(white);
                                  whitePen.Width = 15;
                                  //whitePen.DashStyle = System.Drawing.Drawing2D.DashStyle.Dash;
                                  whitePen.StartCap = System.Drawing.Drawing2D.LineCap.Round;
                                  whitePen.EndCap = System.Drawing.Drawing2D.LineCap.Round;
                                  
                                  //draw Horizental lines
                                  e.Graphics.DrawLine(whitePen, 400, 300, 1050, 300);
                                  e.Graphics.DrawLine(whitePen, 400, 460, 1050, 460);
                      
                                  //draw Vertical lines
                                  e.Graphics.DrawLine(whitePen, 610, 140, 610, 620);
                                  e.Graphics.DrawLine(whitePen, 840, 140, 840, 620);
                      
                                  
                      
                              }
                          }
                      }


## Mask Text Box 

        
        
        using System;
        using System.Windows.Forms;
        
        namespace frMaskTextBox
        {
            public partial class frMaskTextBox : Form
            {
                public frMaskTextBox()
                {
                    InitializeComponent();
                }
        
                private void button1_Click(object sender, EventArgs e)
                {
                    if (maskedTextBox1.MaskFull)
                    {
        
                    }
                }
            }
        }

## Combo Box 

        using System;
        using System.Windows.Forms;
        
        namespace frMaskTextBox
        {
            public partial class CombBox : Form
            {
                public CombBox()
                {
                    InitializeComponent();
                }
        
                private void button1_Click(object sender, EventArgs e)
                {
                    comboBox1.Items.Add("Ali");
                }
        
                private void comboBox1_SelectedIndexChanged(object sender, EventArgs e)
                {
                    MessageBox.Show(comboBox1.Text);
                }
        
                private void CombBox_Load(object sender, EventArgs e)
                {
                    comboBox1.SelectedIndex = 1;
                }
            }
        }

## checked box list and link label

          using System.Windows.Forms;
          
          namespace LinkLable
          {
              public partial class Form1 : Form
              {
                  public Form1()
                  {
                      InitializeComponent();
                  }
          
                  private void linkLabel1_LinkClicked(object sender, LinkLabelLinkClickedEventArgs e)
                  {
                      linkLabel1.LinkVisited = true;
                      System.Diagnostics.Process.Start("http://www.ProgrammingAdvices.com");
          
                  }
          
                  private void button1_Click(object sender, System.EventArgs e)
                  {
                      for (int i = 1; i <= 5; i++)
                      {
                          checkedListBox1.Items.Add("Items" + i);
                      }
                  }
          
          
          
                  private void CheckAllItems_Click(object sender, System.EventArgs e)
                  {
                      for (int i = 0; i < checkedListBox1.Items.Count; i++)
                      {
                          checkedListBox1.SetItemChecked(i, true);
                      }
                  }
          
                  private void UnCheckAllItems_Click(object sender, System.EventArgs e)
                  {
                      for (int i = 0; i < checkedListBox1.Items.Count; i++)
                      {
                          checkedListBox1.SetItemChecked(i, false);
                      }
                  }
          
                  private void RemoveThirdItem_Click(object sender, System.EventArgs e)
                  {
                      if (checkedListBox1.Items.Count > 2)
                      {
                          checkedListBox1.Items.RemoveAt(2);
                      }
                  }
          
                  private void ShowChecdItems_Click(object sender, System.EventArgs e)
                  {
          
                      if (checkedListBox1.CheckedItems.Count > 0)
                      {
                          string CheckedItems = "Checked Items:\n";
                          for (int i = 0; i < checkedListBox1.CheckedItems.Count; i++)
                          {
                              CheckedItems += checkedListBox1.CheckedItems[i].ToString() + " ";
                          }
                          MessageBox.Show(CheckedItems, "seclected items", MessageBoxButtons.OK, MessageBoxIcon.Information);
                      }
                      else
                      {
                          MessageBox.Show("No Items selected.", "Information", MessageBoxButtons.OK, MessageBoxIcon.Warning);
                      }
          
                  }
          
                  private void ShowSelectItems_Click(object sender, System.EventArgs e)
                  {
                      if (checkedListBox1.SelectedItems.Count > 0)
                      {
                          string SelectItems = "Select Items : \n ";
                          for (int i = 0; i < checkedListBox1.SelectedItems.Count; i++)
                          {
                              SelectItems += checkedListBox1.SelectedItems[i].ToString() + " ";
                          }
                          MessageBox.Show(SelectItems, "Select Items", MessageBoxButtons.OK, MessageBoxIcon.Information);
                      }
                      else
                      {
                          MessageBox.Show("No Select Items ", "Select Items", MessageBoxButtons.OK, MessageBoxIcon.Warning);
                      }
          
                  }
              }
          }

## Date Time Picker 
            
            
            using System;
            using System.Windows.Forms;
            
            namespace DateTimePaker
            {
                public partial class DateTimePaker : Form
                {
                    public DateTimePaker()
                    {
                        InitializeComponent();
                    }
            
                    private void button1_Click(object sender, EventArgs e)
                    {
                        MessageBox.Show(dateTimePicker1.Value.ToShortDateString());
                    }
            
                    private void button2_Click(object sender, EventArgs e)
                    {
                        MessageBox.Show(dateTimePicker1.Value.ToLongDateString());
                    }
            
                    private void dateTimePicker1_ValueChanged(object sender, EventArgs e)
                    {
                        label1.Text = dateTimePicker1.Text + Environment.NewLine;
                        label1.Text += dateTimePicker1.Value.ToString("dd-MMM-yyyy") + Environment.NewLine;
                        label1.Text += dateTimePicker1.Value.ToString("dddd-MMM-yyyy") + Environment.NewLine;
                        label1.Text += dateTimePicker1.Value.ToString("MM-dd-yyyy") + Environment.NewLine;
                        label1.Text += dateTimePicker1.Value.ToString("dd/MM/yy") + Environment.NewLine;
                        label1.Text += dateTimePicker1.Value.ToString("dddd-dd-MMM-yyyy") + Environment.NewLine;
                    }
                }
            }

## Month Calendar 

          
          using System;
          using System.Windows.Forms;
          
          namespace DateTimePaker
          {
              public partial class MonthCalnder : Form
              {
                  public MonthCalnder()
                  {
                      InitializeComponent();
                  }
          
                  private void button1_Click(object sender, EventArgs e)
                  {
                      MessageBox.Show(monthCalendar1.SelectionRange.ToString());
                  }
          
                  private void button3_Click(object sender, EventArgs e)
                  {
                      MessageBox.Show(monthCalendar1.SelectionRange.Start.ToShortDateString());
                  }
          
                  private void button2_Click(object sender, EventArgs e)
                  {
                      MessageBox.Show(monthCalendar1.SelectionRange.End.ToShortDateString());
                  }
              }
          }



          
## Timer 

            
            using System;
            using System.Windows.Forms;
            
            namespace DateTimePaker
            {
                public partial class Timer : Form
                {
                    public Timer()
                    {
                        InitializeComponent();
                    }
                    private int Count = 0;
                    private void timer1_Tick(object sender, EventArgs e)
                    {
                        Count++;
                        label1.Text = Count.ToString();
                    }
            
                    private void button1_Click(object sender, EventArgs e)
                    {
                        timer1.Enabled = true;
                    }
            
                    private void button2_Click(object sender, EventArgs e)
                    {
                        timer1.Enabled = false;
                    }
            
                    private void label1_Click(object sender, EventArgs e)
                    {
            
                    }
                }
            }


## NotifyICON 

          using System;
          using System.Drawing;
          using System.Windows.Forms;
          
          namespace DateTimePaker
          {
              public partial class NotifyIcon : Form
              {
                  public NotifyIcon()
                  {
                      InitializeComponent();
                  }
          
                  private void button1_Click(object sender, EventArgs e)
                  {
                      notifyIcon1.Icon = SystemIcons.Application;
                      notifyIcon1.BalloonTipIcon = ToolTipIcon.Error;
                      notifyIcon1.BalloonTipTitle = "This is Title";
                      notifyIcon1.BalloonTipText = "This is a message";
                      notifyIcon1.ShowBalloonTip(10000);
                  }
          
                  private void notifyIcon1_MouseDoubleClick(object sender, MouseEventArgs e)
                  {
                      MessageBox.Show("BalloonTip Clicked");
                  }
              }
          }


## Tree View and Image List 

                using System;
                using System.Windows.Forms;
                
                namespace DateTimePaker
                {
                    public partial class TreeView : Form
                    {
                        public TreeView()
                        {
                            InitializeComponent();
                        }
                
                
                        private void treeView1_MouseDoubleClick(object sender, MouseEventArgs e)
                        {
                            MessageBox.Show(treeView1.SelectedNode.Text);
                        }
                
                        private void treeView1_AfterChecked(object sender, TreeViewEventArgs e)
                        {
                            CheckTreeViewNode(e.Node, e.Node.Checked);
                        }
                
                        private void CheckTreeViewNode(TreeNode node, Boolean isChecked)
                        {
                            foreach (TreeNode item in node.Nodes)
                            {
                                item.Checked = isChecked;
                
                                if (item.Nodes.Count > 0)
                                {
                                    this.CheckTreeViewNode(item, isChecked);
                                }
                            }
                        }
                
                        private void treeView1_AfterSelect(object sender, TreeViewEventArgs e)
                        {
                
                        }
                    }
                }

## Progress Bar

                          using System;
                          using System.Threading;
                          using System.Windows.Forms;
                          
                          namespace DateTimePaker
                          {
                              public partial class ProgressBar : Form
                              {
                                  public ProgressBar()
                                  {
                                      InitializeComponent();
                                  }
                          
                                  private void IncreaseProgress_Click(object sender, EventArgs e)
                                  {
                                      progressBar1.Value = 0;
                                      progressBar1.Maximum = 100;
                                      progressBar1.Minimum = 0;
                          
                                      for (int i = 1; i <= 100; i++)
                                      {
                                          if (progressBar1.Value < progressBar1.Maximum)
                                          {
                                              Thread.Sleep(50);
                                              progressBar1.Value += 1;
                                              label1.Text = (((float)progressBar1.Value / progressBar1.Maximum) * 100) + "%";
                          
                                              progressBar1.Refresh();
                                              label1.Refresh();
                          
                                          }
                                          else
                                          {
                                              IncreaseProgress.Enabled = false;
                                          }
                                      }
                                  }
                          
                                  private void ResetProgress_Click(object sender, EventArgs e)
                                  {
                                      progressBar1.Value = 0;
                                      progressBar1.Maximum = 100;
                                      progressBar1.Minimum = 0;
                                  }
                              }
                          }


## List View 














