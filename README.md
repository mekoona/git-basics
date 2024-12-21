using System;
using System.Windows.Forms;

namespace ProductManagementApp
{
    public class MainForm : Form
    {
        private DataGridView dgvProducts;
        private ComboBox cbSort, cbFilter;
        private TextBox txtSearch;
        private Button btnAdd, btnEdit, btnDelete, btnPrevPage, btnNextPage;
        private FlowLayoutPanel pnlPages;

        public MainForm()
        {
            // Инициализация главной формы
            this.Text = "Список продукции";
            this.Size = new System.Drawing.Size(1000, 600);

            // Панель поиска, фильтрации и сортировки
            var pnlControls = new FlowLayoutPanel
            {
                Dock = DockStyle.Top,
                AutoSize = true,
                Padding = new Padding(10)
            };

            cbSort = new ComboBox
            {
                Width = 150,
                DropDownStyle = ComboBoxStyle.DropDownList
            };
            cbSort.Items.AddRange(new string[] { "Наименование", "Цех", "Минимальная стоимость" });

            cbFilter = new ComboBox
            {
                Width = 150,
                DropDownStyle = ComboBoxStyle.DropDownList
            };
            cbFilter.Items.Add("Все типы"); // Первым элементом "Все типы"

            txtSearch = new TextBox
            {
                Width = 200,
                PlaceholderText = "Поиск..."
            };

            pnlControls.Controls.Add(new Label { Text = "Сортировка:", AutoSize = true });
            pnlControls.Controls.Add(cbSort);
            pnlControls.Controls.Add(new Label { Text = "Фильтр:", AutoSize = true });
            pnlControls.Controls.Add(cbFilter);
            pnlControls.Controls.Add(new Label { Text = "Поиск:", AutoSize = true });
            pnlControls.Controls.Add(txtSearch);

            // Таблица для отображения продукции
            dgvProducts = new DataGridView
            {
                Dock = DockStyle.Fill,
                ReadOnly = true,
                SelectionMode = DataGridViewSelectionMode.FullRowSelect,
                MultiSelect = true,
                AllowUserToAddRows = false,
                AutoSizeColumnsMode = DataGridViewAutoSizeColumnsMode.Fill
            };

            // Панель для кнопок
            var pnlButtons = new FlowLayoutPanel
            {
                Dock = DockStyle.Bottom,
                AutoSize = true,
                Padding = new Padding(10)
            };

            btnAdd = new Button { Text = "Добавить", Width = 100 };
            btnEdit = new Button { Text = "Редактировать", Width = 100 };
            btnDelete = new Button { Text = "Удалить", Width = 100 };
            pnlButtons.Controls.Add(btnAdd);
            pnlButtons.Controls.Add(btnEdit);
            pnlButtons.Controls.Add(btnDelete);

            // Панель для навигации по страницам
            pnlPages = new FlowLayoutPanel
            {
                Dock = DockStyle.Bottom,
                AutoSize = true,
                Padding = new Padding(10)
            };

            btnPrevPage = new Button { Text = "←", Width = 50 };
            btnNextPage = new Button { Text = "→", Width = 50 };

            pnlPages.Controls.Add(btnPrevPage);
            pnlPages.Controls.Add(btnNextPage);

            // Добавление элементов на главную форму
            this.Controls.Add(dgvProducts);
            this.Controls.Add(pnlControls);
            this.Controls.Add(pnlButtons);
            this.Controls.Add(pnlPages);
        }

        [STAThread]
        public static void Main()
        {
            Application.EnableVisualStyles();
            Application.Run(new MainForm());
        }
    }
}
