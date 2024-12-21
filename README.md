using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace WindowsFormsApp1
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
            InitializeCustomComponents();
        }

        private void InitializeCustomComponents()
        {
            // Установка заголовка, иконки и размера формы
            this.Text = "Список продукции";
            this.Icon = new Icon("your_icon.ico"); // Укажите путь к иконке
            this.Size = new Size(1000, 600);
            this.BackColor = Color.White;

            // Установка шрифта
            Font defaultFont = new Font("Tw Cen MT", 10, FontStyle.Regular);

            // Верхняя панель с заголовком и логотипом
            Panel headerPanel = new Panel
            {
                Dock = DockStyle.Top,
                Height = 80,
                BackColor = ColorTranslator.FromHtml("#B0E5FD")
            };

            PictureBox logo = new PictureBox
            {
                Image = Image.FromFile("your_logo.png"), // Укажите путь к логотипу
                SizeMode = PictureBoxSizeMode.StretchImage,
                Size = new Size(60, 60),
                Location = new Point(10, 10)
            };

            Label headerLabel = new Label
            {
                Text = "Управление продукцией",
                Font = new Font("Tw Cen MT", 16, FontStyle.Bold),
                AutoSize = true,
                Location = new Point(80, 25),
                ForeColor = Color.Black
            };

            headerPanel.Controls.Add(logo);
            headerPanel.Controls.Add(headerLabel);

            // Панель управления (сортировка, фильтрация, поиск)
            FlowLayoutPanel controlPanel = new FlowLayoutPanel
            {
                Dock = DockStyle.Top,
                AutoSize = true,
                Padding = new Padding(10),
                BackColor = Color.White,
                FlowDirection = FlowDirection.LeftToRight
            };

            Label lblSort = new Label
            {
                Text = "Сортировка:",
                AutoSize = true,
                Font = defaultFont,
                ForeColor = Color.Black
            };

            ComboBox cbSort = new ComboBox
            {
                Width = 150,
                DropDownStyle = ComboBoxStyle.DropDownList,
                Font = defaultFont,
                Name = "cbSort"
            };
            cbSort.Items.AddRange(new string[] { "Наименование", "Цех", "Минимальная стоимость" });

            Label lblFilter = new Label
            {
                Text = "Фильтр:",
                AutoSize = true,
                Font = defaultFont,
                ForeColor = Color.Black
            };

            ComboBox cbFilter = new ComboBox
            {
                Width = 150,
                DropDownStyle = ComboBoxStyle.DropDownList,
                Font = defaultFont,
                Name = "cbFilter"
            };
            cbFilter.Items.Add("Все типы");

            Label lblSearch = new Label
            {
                Text = "Поиск:",
                AutoSize = true,
                Font = defaultFont,
                ForeColor = Color.Black
            };

            TextBox txtSearch = new TextBox
            {
                Width = 200,
                Font = defaultFont,
                Name = "txtSearch"
            };

            controlPanel.Controls.Add(lblSort);
            controlPanel.Controls.Add(cbSort);
            controlPanel.Controls.Add(lblFilter);
            controlPanel.Controls.Add(cbFilter);
            controlPanel.Controls.Add(lblSearch);
            controlPanel.Controls.Add(txtSearch);

            // Центральная таблица
            DataGridView dgvProducts = new DataGridView
            {
                Dock = DockStyle.Fill,
                ReadOnly = true,
                MultiSelect = true,
                Name = "dgvProducts",
                AllowUserToAddRows = false,
                AutoSizeColumnsMode = DataGridViewAutoSizeColumnsMode.Fill,
                BackgroundColor = Color.White,
                Font = defaultFont
            };

            // Панель для кнопок управления
            FlowLayoutPanel buttonPanel = new FlowLayoutPanel
            {
                Dock = DockStyle.Bottom,
                AutoSize = true,
                Padding = new Padding(10),
                BackColor = Color.White
            };

            Button btnAdd = new Button
            {
                Text = "Добавить",
                Width = 120,
                BackColor = ColorTranslator.FromHtml("#FDBD40"),
                Font = defaultFont,
                Name = "btnAdd"
            };

            Button btnEdit = new Button
            {
                Text = "Редактировать",
                Width = 120,
                BackColor = ColorTranslator.FromHtml("#FDBD40"),
                Font = defaultFont,
                Name = "btnEdit"
            };

            Button btnDelete = new Button
            {
                Text = "Удалить",
                Width = 120,
                BackColor = ColorTranslator.FromHtml("#FDBD40"),
                Font = defaultFont,
                Name = "btnDelete"
            };

            buttonPanel.Controls.Add(btnAdd);
            buttonPanel.Controls.Add(btnEdit);
            buttonPanel.Controls.Add(btnDelete);

            // Панель для навигации по страницам
            FlowLayoutPanel pagePanel = new FlowLayoutPanel
            {
                Dock = DockStyle.Bottom,
                AutoSize = true,
                Padding = new Padding(10),
                BackColor = Color.White
            };

            Button btnPrevPage = new Button
            {
                Text = "←",
                Width = 50,
                BackColor = ColorTranslator.FromHtml("#B0E5FD"),
                Font = defaultFont,
                Name = "btnPrevPage"
            };

            Button btnNextPage = new Button
            {
                Text = "→",
                Width = 50,
                BackColor = ColorTranslator.FromHtml("#B0E5FD"),
                Font = defaultFont,
                Name = "btnNextPage"
            };

            pagePanel.Controls.Add(btnPrevPage);
            pagePanel.Controls.Add(btnNextPage);

            // Добавление всех элементов на форму
            this.Controls.Add(dgvProducts);
            this.Controls.Add(headerPanel);
            this.Controls.Add(controlPanel);
            this.Controls.Add(buttonPanel);
            this.Controls.Add(pagePanel);
        }
    }
}
