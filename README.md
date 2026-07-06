<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>CITI Rights Management • elevated</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" />
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,400;14..32,500;14..32,600;14..32,700&display=swap" rel="stylesheet" />
    <style>
        /* ── Reset & Base ── */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            background: #f4f6fa;
            padding: 24px 32px;
            color: #0e1a2b;
            line-height: 1.5;
        }

        /* ── CITI Colors ── */
        :root {
            --citi-dark: #0E1632;
            --citi-blue: #255AE3;
            --citi-blue-light: #2559E1;
            --citi-gray: #F3F2F1;
            --citi-gray-light: #f8fafd;
            --citi-border: #e6edf5;
            --citi-shadow-sm: 0 2px 8px rgba(14, 22, 50, 0.06);
            --citi-shadow-md: 0 8px 32px rgba(14, 22, 50, 0.08);
            --citi-shadow-lg: 0 16px 48px rgba(14, 22, 50, 0.12);
            --citi-radius: 16px;
            --citi-radius-sm: 10px;
            --citi-transition: 0.25s cubic-bezier(0.2, 0, 0, 1);
        }

        /* ── Scrollbar ── */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #eef2f6;
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb {
            background: var(--citi-blue);
            border-radius: 10px;
        }

        /* ── Typography ── */
        .text-xs {
            font-size: 11px;
            letter-spacing: 0.3px;
        }
        .text-sm {
            font-size: 12px;
        }
        .text-muted {
            color: #6b7a8f;
        }
        .fw-600 {
            font-weight: 600;
        }

        /* ── Layout ── */
        .app-container {
            max-width: 1600px;
            margin: 0 auto;
        }

        /* ── Cards ── */
        .card {
            background: #ffffff;
            border-radius: var(--citi-radius);
            box-shadow: var(--citi-shadow-sm);
            border: 1px solid rgba(230, 237, 245, 0.6);
            overflow: hidden;
            transition: box-shadow var(--citi-transition), transform var(--citi-transition);
            height: 100%;
            display: flex;
            flex-direction: column;
            backdrop-filter: blur(2px);
        }
        .card:hover {
            box-shadow: var(--citi-shadow-md);
            transform: translateY(-2px);
        }

        .card-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 14px 18px;
            background: var(--citi-gray-light);
            border-bottom: 1px solid var(--citi-border);
            flex-shrink: 0;
            gap: 10px;
            flex-wrap: wrap;
        }
        .card-header .title-group {
            display: flex;
            align-items: center;
            gap: 12px;
        }
        .card-header .title-group .icon-wrap {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 34px;
            height: 34px;
            background: linear-gradient(135deg, var(--citi-blue), #1a45b0);
            border-radius: var(--citi-radius-sm);
            color: #fff;
            font-size: 15px;
            box-shadow: 0 4px 8px rgba(37, 90, 227, 0.2);
        }
        .card-header .title-group h6 {
            font-size: 12px;
            font-weight: 700;
            color: var(--citi-dark);
            margin: 0;
            letter-spacing: 0.5px;
            text-transform: uppercase;
            opacity: 0.8;
        }
        .card-header .title-group .badge-count {
            background: var(--citi-dark);
            color: #fff;
            font-size: 10px;
            padding: 0 10px;
            border-radius: 30px;
            font-weight: 600;
            line-height: 22px;
            margin-left: 4px;
            opacity: 0.9;
        }
        .card-header .actions {
            display: flex;
            align-items: center;
            gap: 6px;
            flex-wrap: wrap;
        }

        .card-body {
            padding: 0;
            flex: 1;
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }
        .card-body .table-wrap {
            overflow-y: auto;
            flex: 1;
            padding: 0 6px 6px 6px;
        }

        /* ── Tables ── */
        .citi-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 12px;
        }
        .citi-table thead {
            position: sticky;
            top: 0;
            z-index: 5;
        }
        .citi-table thead th {
            background: #f1f5fb;
            color: var(--citi-dark);
            font-weight: 600;
            font-size: 10px;
            text-transform: uppercase;
            letter-spacing: 0.6px;
            padding: 10px 12px;
            text-align: left;
            border-bottom: 2px solid var(--citi-border);
            white-space: nowrap;
        }
        .citi-table tbody tr {
            transition: background 0.15s ease, box-shadow 0.15s ease;
            border-bottom: 1px solid #f1f5fb;
        }
        .citi-table tbody tr:hover {
            background: #f8fcff;
        }
        .citi-table tbody tr.selected {
            background: #eaf1fe !important;
            border-left: 3px solid var(--citi-blue);
            box-shadow: inset 0 0 0 1px rgba(37, 90, 227, 0.1);
        }
        .citi-table tbody td {
            padding: 9px 12px;
            vertical-align: middle;
            font-size: 12px;
            color: #1e293b;
        }

        /* ── Buttons & Controls ── */
        .btn-icon {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 30px;
            height: 30px;
            border: none;
            border-radius: var(--citi-radius-sm);
            background: transparent;
            color: #6b7a8f;
            cursor: pointer;
            transition: all 0.15s ease;
            font-size: 13px;
        }
        .btn-icon:hover {
            background: #eef2f6;
            color: var(--citi-dark);
        }
        .btn-icon.primary {
            color: var(--citi-blue);
        }
        .btn-icon.primary:hover {
            background: #e6edfb;
        }
        .btn-icon.danger {
            color: #dc2626;
        }
        .btn-icon.danger:hover {
            background: #fee2e2;
        }
        .btn-icon.success {
            color: #16a34a;
        }
        .btn-icon.success:hover {
            background: #dcfce7;
        }
        .btn-icon.warning {
            color: #d97706;
        }
        .btn-icon.warning:hover {
            background: #fef3c7;
        }

        .btn-sm {
            display: inline-flex;
            align-items: center;
            gap: 6px;
            padding: 6px 14px;
            border: none;
            border-radius: 30px;
            font-size: 11px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s ease;
            background: var(--citi-gray);
            color: var(--citi-dark);
            letter-spacing: 0.2px;
            box-shadow: 0 1px 2px rgba(0,0,0,0.02);
        }
        .btn-sm:hover {
            background: #e2e8f0;
            transform: translateY(-1px);
        }
        .btn-sm.primary {
            background: linear-gradient(135deg, var(--citi-blue), #1a45b0);
            color: #fff;
            box-shadow: 0 4px 12px rgba(37, 90, 227, 0.25);
        }
        .btn-sm.primary:hover {
            background: linear-gradient(135deg, #1a45b0, #0f3378);
            box-shadow: 0 6px 16px rgba(37, 90, 227, 0.35);
            transform: translateY(-2px);
        }
        .btn-sm.outline {
            background: transparent;
            border: 1px solid var(--citi-border);
        }
        .btn-sm.outline:hover {
            background: var(--citi-gray);
        }
        .btn-sm.danger {
            background: #dc2626;
            color: #fff;
        }
        .btn-sm.danger:hover {
            background: #b91c1c;
        }

        /* ── Inputs / Selects ── */
        .citi-input {
            padding: 6px 12px;
            border: 1px solid var(--citi-border);
            border-radius: 30px;
            font-size: 12px;
            background: #fff;
            transition: all 0.2s ease;
            outline: none;
            width: 100%;
            font-family: inherit;
            box-shadow: 0 1px 2px rgba(0,0,0,0.02);
        }
        .citi-input:focus {
            border-color: var(--citi-blue);
            box-shadow: 0 0 0 4px rgba(37, 90, 227, 0.12);
        }
        .citi-input::placeholder {
            color: #94a3b8;
        }

        .citi-select {
            padding: 6px 12px;
            border: 1px solid var(--citi-border);
            border-radius: 30px;
            font-size: 12px;
            background: #fff;
            outline: none;
            width: 100%;
            font-family: inherit;
            appearance: auto;
            box-shadow: 0 1px 2px rgba(0,0,0,0.02);
        }
        .citi-select:focus {
            border-color: var(--citi-blue);
            box-shadow: 0 0 0 4px rgba(37, 90, 227, 0.12);
        }

        .citi-checkbox {
            width: 16px;
            height: 16px;
            accent-color: var(--citi-blue);
            cursor: pointer;
            border-radius: 4px;
            border: 1.5px solid #cbd5e1;
            transition: all 0.15s ease;
        }
        .citi-checkbox:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        /* ── Pagination ── */
        .pagination-bar {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 10px 16px;
            border-top: 1px solid var(--citi-border);
            background: var(--citi-gray-light);
            flex-shrink: 0;
            flex-wrap: wrap;
            gap: 6px;
        }
        .pagination-bar .info {
            font-size: 11px;
            color: #6b7a8f;
        }
        .pagination-bar .controls {
            display: flex;
            align-items: center;
            gap: 4px;
        }
        .pagination-bar .controls button {
            width: 30px;
            height: 30px;
            border: 1px solid var(--citi-border);
            border-radius: var(--citi-radius-sm);
            background: #fff;
            color: var(--citi-dark);
            font-size: 12px;
            cursor: pointer;
            transition: all 0.15s ease;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            font-weight: 500;
        }
        .pagination-bar .controls button:hover:not(:disabled) {
            background: var(--citi-blue);
            color: #fff;
            border-color: var(--citi-blue);
            box-shadow: 0 2px 8px rgba(37, 90, 227, 0.2);
        }
        .pagination-bar .controls button:disabled {
            opacity: 0.3;
            cursor: not-allowed;
        }
        .pagination-bar .controls button.active {
            background: var(--citi-blue);
            color: #fff;
            border-color: var(--citi-blue);
            box-shadow: 0 2px 8px rgba(37, 90, 227, 0.2);
        }

        /* ── Main Header ── */
        .main-header {
            background: linear-gradient(135deg, var(--citi-dark), #1a2744);
            border-radius: var(--citi-radius);
            padding: 20px 32px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 28px;
            box-shadow: var(--citi-shadow-lg);
            flex-wrap: wrap;
            gap: 16px;
            border: 1px solid rgba(255,255,255,0.05);
        }
        .main-header .brand {
            display: flex;
            align-items: center;
            gap: 18px;
        }
        .main-header .brand .logo-icon {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 46px;
            height: 46px;
            background: linear-gradient(135deg, var(--citi-blue), #1a45b0);
            border-radius: var(--citi-radius-sm);
            color: #fff;
            font-size: 22px;
            box-shadow: 0 6px 16px rgba(37, 90, 227, 0.3);
        }
        .main-header .brand h4 {
            color: #fff;
            font-weight: 700;
            font-size: 22px;
            margin: 0;
            letter-spacing: -0.3px;
            display: flex;
            align-items: baseline;
            gap: 8px;
        }
        .main-header .brand h4 span {
            font-weight: 400;
            opacity: 0.5;
            font-size: 14px;
            letter-spacing: 0.3px;
        }
        .main-header .user-badge {
            display: flex;
            align-items: center;
            gap: 14px;
            background: rgba(255,255,255,0.06);
            padding: 6px 18px 6px 12px;
            border-radius: 40px;
            border: 1px solid rgba(255,255,255,0.08);
            backdrop-filter: blur(4px);
        }
        .main-header .user-badge .avatar {
            width: 36px;
            height: 36px;
            border-radius: 50%;
            background: linear-gradient(135deg, #255AE3, #6d8df0);
            color: #fff;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 14px;
            font-weight: 600;
            box-shadow: 0 4px 10px rgba(37, 90, 227, 0.3);
        }
        .main-header .user-badge .name {
            color: #fff;
            font-size: 14px;
            font-weight: 500;
        }
        .main-header .user-badge .name small {
            font-weight: 400;
            opacity: 0.5;
            font-size: 11px;
            display: block;
            margin-top: -2px;
        }

        /* ── Empty state / placeholder ── */
        .empty-state {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 36px 16px;
            color: #94a3b8;
            text-align: center;
        }
        .empty-state .icon {
            font-size: 36px;
            margin-bottom: 12px;
            opacity: 0.3;
        }
        .empty-state strong {
            color: #6b7a8f;
            font-weight: 500;
        }
        .empty-state small {
            font-size: 12px;
            opacity: 0.6;
        }

        /* ── Message banner ── */
        .msg-banner {
            padding: 12px 18px;
            background: #fffbeb;
            border-left: 4px solid #f59e0b;
            color: #92400e;
            font-size: 13px;
            display: flex;
            align-items: center;
            gap: 12px;
            border-radius: var(--citi-radius-sm);
            margin: 6px;
        }
        .msg-banner strong {
            font-weight: 600;
        }

        /* ── Checklist ── */
        .checklist-wrap {
            background: #fff;
            border-radius: var(--citi-radius);
            box-shadow: var(--citi-shadow-sm);
            border: 1px solid rgba(230, 237, 245, 0.6);
            overflow: hidden;
            margin-top: 16px;
            transition: box-shadow var(--citi-transition);
        }
        .checklist-wrap:hover {
            box-shadow: var(--citi-shadow-md);
        }
        .checklist-wrap .cl-header {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 14px 20px;
            background: var(--citi-gray-light);
            border-bottom: 1px solid var(--citi-border);
        }
        .checklist-wrap .cl-header .icon {
            color: var(--citi-blue);
            font-size: 18px;
        }
        .checklist-wrap .cl-header h6 {
            font-size: 12px;
            font-weight: 700;
            color: var(--citi-dark);
            margin: 0;
            text-transform: uppercase;
            letter-spacing: 0.6px;
        }
        .checklist-wrap .cl-header .count-badge {
            margin-left: auto;
            background: var(--citi-blue);
            color: #fff;
            font-size: 10px;
            padding: 0 12px;
            border-radius: 30px;
            line-height: 24px;
            font-weight: 600;
        }
        .checklist-wrap .cl-body {
            padding: 6px 20px 12px;
            max-height: 140px;
            overflow-y: auto;
        }
        .checklist-wrap .cl-body .cl-item {
            display: flex;
            align-items: center;
            gap: 14px;
            padding: 8px 0;
            font-size: 12px;
            border-bottom: 1px solid #f1f5fb;
        }
        .checklist-wrap .cl-body .cl-item:last-child {
            border-bottom: none;
        }
        .checklist-wrap .cl-body .cl-item .dot {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background: var(--citi-blue);
            flex-shrink: 0;
            box-shadow: 0 2px 4px rgba(37, 90, 227, 0.2);
        }
        .checklist-wrap .cl-body .cl-item .action {
            font-weight: 600;
            color: var(--citi-dark);
            min-width: 90px;
        }
        .checklist-wrap .cl-body .cl-item .desc {
            color: #475569;
        }
        .checklist-wrap .cl-body .cl-item .time {
            margin-left: auto;
            font-size: 10px;
            color: #94a3b8;
            white-space: nowrap;
        }

        /* ── Modal ── */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(14, 22, 50, 0.5);
            backdrop-filter: blur(8px);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 2000;
            padding: 20px;
            animation: fadeIn 0.25s ease;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        .modal-box {
            background: #fff;
            border-radius: var(--citi-radius);
            padding: 32px 36px;
            max-width: 480px;
            width: 100%;
            box-shadow: var(--citi-shadow-lg);
            animation: slideUp 0.3s ease;
        }
        @keyframes slideUp {
            from { opacity: 0; transform: translateY(20px) scale(0.96); }
            to { opacity: 1; transform: translateY(0) scale(1); }
        }
        .modal-box h5 {
            font-size: 20px;
            font-weight: 700;
            color: var(--citi-dark);
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .modal-box h5 i {
            color: var(--citi-blue);
        }
        .modal-box .field {
            margin-bottom: 16px;
        }
        .modal-box .field label {
            display: block;
            font-size: 12px;
            font-weight: 600;
            color: #475569;
            margin-bottom: 4px;
            letter-spacing: 0.3px;
        }
        .modal-box .actions {
            display: flex;
            justify-content: flex-end;
            gap: 10px;
            margin-top: 24px;
        }

        /* ── Grid ── */
        .grid-top {
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 18px;
            margin-bottom: 18px;
        }
        .grid-bottom {
            display: grid;
            grid-template-columns: 1fr 1fr 1.2fr;
            gap: 18px;
            margin-bottom: 18px;
        }

        /* ── Right detail expand ── */
        .right-detail-box {
            background: #f8fcff;
            border: 1px solid #e6edfb;
            border-radius: var(--citi-radius-sm);
            padding: 12px 16px;
            margin: 4px 0;
        }
        .right-detail-box .row {
            display: flex;
            align-items: center;
            gap: 16px;
            flex-wrap: wrap;
        }
        .right-detail-box .row label {
            display: flex;
            align-items: center;
            gap: 6px;
            font-size: 12px;
            color: #1e293b;
            cursor: pointer;
            font-weight: 500;
        }
        .right-detail-box .row label input[type="checkbox"] {
            width: 14px;
            height: 14px;
            accent-color: var(--citi-blue);
            cursor: pointer;
        }

        /* ── Responsive ── */
        @media (max-width: 1200px) {
            .grid-bottom {
                grid-template-columns: 1fr 1fr;
            }
        }
        @media (max-width: 992px) {
            .grid-top {
                grid-template-columns: 1fr;
            }
            .grid-bottom {
                grid-template-columns: 1fr;
            }
        }
        @media (max-width: 600px) {
            body {
                padding: 12px;
            }
            .main-header {
                flex-direction: column;
                align-items: stretch;
                text-align: center;
                padding: 18px 16px;
            }
            .main-header .brand {
                justify-content: center;
            }
            .main-header .user-badge {
                justify-content: center;
            }
            .modal-box {
                padding: 24px 20px;
            }
            .card-header {
                flex-direction: column;
                align-items: stretch;
                gap: 8px;
            }
            .card-header .actions {
                justify-content: flex-start;
            }
        }
    </style>
</head>
<body>

    <div class="app-container">

        <!-- ===== MAIN HEADER ===== -->
        <header class="main-header">
            <div class="brand">
                <div class="logo-icon">
                    <i class="fas fa-shield-halved"></i>
                </div>
                <h4>
                    Rights Management
                    <span>· CITI Access</span>
                </h4>
            </div>
            <div class="user-badge">
                <div class="avatar">JD</div>
                <div class="name">
                    John Doe
                    <small>Admin · System</small>
                </div>
                <button class="btn-icon" style="color:rgba(255,255,255,0.4);" title="Profile">
                    <i class="fas fa-chevron-down"></i>
                </button>
            </div>
        </header>

        <!-- ===== TOP ROW: Users + Depts ===== -->
        <div class="grid-top">

            <!-- Users Grid -->
            <div class="card">
                <div class="card-header">
                    <div class="title-group">
                        <div class="icon-wrap"><i class="fas fa-users"></i></div>
                        <h6>Users</h6>
                        <span class="badge-count">24</span>
                    </div>
                    <div class="actions">
                        <button class="btn-sm primary" onclick="document.getElementById('addUserModal').style.display='flex'">
                            <i class="fas fa-plus"></i> Add New
                        </button>
                        <button class="btn-sm outline" onclick="alert('Refreshed')">
                            <i class="fas fa-sync-alt"></i>
                        </button>
                        <label style="display:flex;align-items:center;gap:6px;font-size:11px;color:#475569;cursor:pointer;background:#f1f5fb;padding:2px 10px 2px 6px;border-radius:30px;">
                            <input type="checkbox" class="citi-checkbox" style="width:14px;height:14px;" /> Show Terminated
                        </label>
                        <div style="display:flex;align-items:center;gap:4px;">
                            <input class="citi-input" placeholder="Search..." style="width:120px;" />
                            <button class="btn-sm outline"><i class="fas fa-filter"></i></button>
                        </div>
                    </div>
                </div>
                <div class="card-body">
                    <div class="table-wrap" style="max-height:260px;">
                        <table class="citi-table">
                            <thead>
                                <tr>
                                    <th style="width:70px;">Actions</th>
                                    <th>User Id</th>
                                    <th>First Name</th>
                                    <th>Last Name</th>
                                    <th>Default Dept.</th>
                                    <th style="width:70px;">Term.</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr class="selected">
                                    <td>
                                        <button class="btn-icon primary" title="Edit"><i class="fas fa-pen"></i></button>
                                        <button class="btn-icon danger" title="Terminate"><i class="fas fa-ban"></i></button>
                                    </td>
                                    <td><strong class="fw-600">jsmith</strong></td>
                                    <td>John</td>
                                    <td>Smith</td>
                                    <td>Engineering</td>
                                    <td><input type="checkbox" class="citi-checkbox" disabled /></td>
                                </tr>
                                <tr>
                                    <td>
                                        <button class="btn-icon primary" title="Edit"><i class="fas fa-pen"></i></button>
                                        <button class="btn-icon danger" title="Terminate"><i class="fas fa-ban"></i></button>
                                    </td>
                                    <td><strong class="fw-600">mjohnson</strong></td>
                                    <td>Mary</td>
                                    <td>Johnson</td>
                                    <td>Finance</td>
                                    <td><input type="checkbox" class="citi-checkbox" disabled /></td>
                                </tr>
                                <tr>
                                    <td>
                                        <button class="btn-icon primary" title="Edit"><i class="fas fa-pen"></i></button>
                                        <button class="btn-icon danger" title="Terminate"><i class="fas fa-ban"></i></button>
                                    </td>
                                    <td><strong class="fw-600">bwilliams</strong></td>
                                    <td>Bob</td>
                                    <td>Williams</td>
                                    <td>IT</td>
                                    <td><input type="checkbox" class="citi-checkbox" disabled /></td>
                                </tr>
                                <tr>
                                    <td colspan="6" style="text-align:center;color:#94a3b8;padding:24px 0;">
                                        <i class="fas fa-inbox" style="font-size:22px;display:block;margin-bottom:8px;opacity:0.3;"></i>
                                        No more records
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    <div class="pagination-bar">
                        <span class="info">Showing 1–3 of 24</span>
                        <div class="controls">
                            <button disabled><i class="fas fa-chevron-left"></i></button>
                            <button class="active">1</button>
                            <button>2</button>
                            <button>3</button>
                            <button>…</button>
                            <button>8</button>
                            <button><i class="fas fa-chevron-right"></i></button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- User Depts Grid -->
            <div class="card">
                <div class="card-header">
                    <div class="title-group">
                        <div class="icon-wrap" style="background:linear-gradient(135deg,#1e293b,#0f172a);"><i class="fas fa-sitemap"></i></div>
                        <h6>User Departments</h6>
                        <span class="badge-count">3</span>
                    </div>
                    <button class="btn-sm outline" onclick="alert('Refreshed')">
                        <i class="fas fa-sync-alt"></i>
                    </button>
                </div>
                <div class="card-body">
                    <div class="table-wrap" style="max-height:260px;">
                        <table class="citi-table">
                            <thead>
                                <tr>
                                    <th style="width:30px;"></th>
                                    <th style="width:40px;"></th>
                                    <th>Department</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td><input type="checkbox" class="citi-checkbox" checked disabled /></td>
                                    <td><button class="btn-icon" title="Filter"><i class="fas fa-search"></i></button></td>
                                    <td>
                                        <button class="btn-icon danger" style="margin-right:8px;" title="Remove"><i class="fas fa-minus-circle"></i></button>
                                        <span class="fw-600">Engineering</span>
                                    </td>
                                </tr>
                                <tr>
                                    <td><input type="checkbox" class="citi-checkbox" disabled /></td>
                                    <td><button class="btn-icon" title="Filter"><i class="fas fa-search"></i></button></td>
                                    <td>
                                        <button class="btn-icon success" style="margin-right:8px;" title="Assign"><i class="fas fa-plus-circle"></i></button>
                                        Finance
                                    </td>
                                </tr>
                                <tr>
                                    <td><input type="checkbox" class="citi-checkbox" disabled /></td>
                                    <td><button class="btn-icon" title="Filter"><i class="fas fa-search"></i></button></td>
                                    <td>
                                        <button class="btn-icon success" style="margin-right:8px;" title="Assign"><i class="fas fa-plus-circle"></i></button>
                                        IT
                                    </td>
                                </tr>
                                <tr>
                                    <td colspan="3" style="text-align:center;color:#94a3b8;padding:12px 0;">
                                        <i class="fas fa-ellipsis-h" style="opacity:0.3;"></i>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    <div class="pagination-bar">
                        <span class="info">3 departments</span>
                        <div class="controls">
                            <button disabled><i class="fas fa-chevron-left"></i></button>
                            <button class="active">1</button>
                            <button><i class="fas fa-chevron-right"></i></button>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- ===== BOTTOM ROW: Apps + Menus + Rights ===== -->
        <div class="grid-bottom">

            <!-- User Apps -->
            <div class="card">
                <div class="card-header">
                    <div class="title-group">
                        <div class="icon-wrap" style="background:linear-gradient(135deg,#0E1632,#1a2744);"><i class="fas fa-th-large"></i></div>
                        <h6>User Apps</h6>
                        <span class="badge-count">6</span>
                    </div>
                    <button class="btn-sm outline" onclick="alert('Refreshed')">
                        <i class="fas fa-sync-alt"></i>
                    </button>
                </div>
                <div class="card-body">
                    <div class="table-wrap" style="max-height:220px;">
                        <table class="citi-table">
                            <thead>
                                <tr>
                                    <th style="width:30px;"></th>
                                    <th style="width:30px;"></th>
                                    <th style="width:30px;"></th>
                                    <th style="width:30px;"></th>
                                    <th>Application</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr class="selected">
                                    <td><input type="checkbox" class="citi-checkbox" checked disabled /></td>
                                    <td><button class="btn-icon"><i class="fas fa-search"></i></button></td>
                                    <td><button class="btn-icon danger" title="Remove"><i class="fas fa-minus-circle"></i></button></td>
                                    <td><button class="btn-icon warning" title="Suspend"><i class="fas fa-pause-circle"></i></button></td>
                                    <td><strong class="fw-600">Core Banking</strong></td>
                                </tr>
                                <tr>
                                    <td><input type="checkbox" class="citi-checkbox" checked disabled /></td>
                                    <td><button class="btn-icon"><i class="fas fa-search"></i></button></td>
                                    <td><button class="btn-icon danger" title="Remove"><i class="fas fa-minus-circle"></i></button></td>
                                    <td><button class="btn-icon success" title="Enable"><i class="fas fa-play-circle"></i></button></td>
                                    <td>Trade Portal</td>
                                </tr>
                                <tr>
                                    <td><input type="checkbox" class="citi-checkbox" disabled /></td>
                                    <td><button class="btn-icon"><i class="fas fa-search"></i></button></td>
                                    <td><button class="btn-icon success" title="Assign"><i class="fas fa-plus-circle"></i></button></td>
                                    <td><button class="btn-icon" disabled style="opacity:0.2;"><i class="fas fa-circle"></i></button></td>
                                    <td>Risk Engine</td>
                                </tr>
                                <tr>
                                    <td colspan="5" style="text-align:center;color:#94a3b8;padding:8px 0;font-size:11px;">
                                        <i class="fas fa-chevron-down" style="opacity:0.2;"></i>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    <div class="pagination-bar">
                        <span class="info">1–3 of 6</span>
                        <div class="controls">
                            <button disabled><i class="fas fa-chevron-left"></i></button>
                            <button class="active">1</button>
                            <button>2</button>
                            <button><i class="fas fa-chevron-right"></i></button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- User App Menus -->
            <div class="card">
                <div class="card-header">
                    <div class="title-group">
                        <div class="icon-wrap" style="background:linear-gradient(135deg,#1e293b,#0f172a);"><i class="fas fa-list"></i></div>
                        <h6>User App Menus</h6>
                        <span class="badge-count">8</span>
                    </div>
                    <button class="btn-sm outline" onclick="alert('Refreshed')">
                        <i class="fas fa-sync-alt"></i>
                    </button>
                </div>
                <div class="card-body">
                    <div class="table-wrap" style="max-height:220px;">
                        <table class="citi-table">
                            <thead>
                                <tr>
                                    <th style="width:30px;"></th>
                                    <th style="width:40px;"></th>
                                    <th>Menu</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr class="selected">
                                    <td><input type="checkbox" class="citi-checkbox" checked disabled /></td>
                                    <td><button class="btn-icon danger" title="Remove"><i class="fas fa-minus-circle"></i></button></td>
                                    <td><strong class="fw-600">Dashboard</strong></td>
                                </tr>
                                <tr>
                                    <td><input type="checkbox" class="citi-checkbox" checked disabled /></td>
                                    <td><button class="btn-icon danger" title="Remove"><i class="fas fa-minus-circle"></i></button></td>
                                    <td>Transactions</td>
                                </tr>
                                <tr>
                                    <td><input type="checkbox" class="citi-checkbox" disabled /></td>
                                    <td><button class="btn-icon success" title="Assign"><i class="fas fa-plus-circle"></i></button></td>
                                    <td>Reports</td>
                                </tr>
                                <tr>
                                    <td><input type="checkbox" class="citi-checkbox" disabled /></td>
                                    <td><button class="btn-icon success" title="Assign"><i class="fas fa-plus-circle"></i></button></td>
                                    <td>Admin Settings</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    <div class="pagination-bar">
                        <span class="info">1–4 of 8</span>
                        <div class="controls">
                            <button disabled><i class="fas fa-chevron-left"></i></button>
                            <button class="active">1</button>
                            <button>2</button>
                            <button><i class="fas fa-chevron-right"></i></button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- User App Rights -->
            <div class="card">
                <div class="card-header">
                    <div class="title-group">
                        <div class="icon-wrap" style="background:linear-gradient(135deg,#0E1632,#1a2744);"><i class="fas fa-lock"></i></div>
                        <h6>User App Rights</h6>
                        <span class="badge-count">5</span>
                    </div>
                    <button class="btn-sm outline" onclick="alert('Refreshed')">
                        <i class="fas fa-sync-alt"></i>
                    </button>
                </div>
                <div class="card-body">
                    <div class="table-wrap" style="max-height:220px;">
                        <table class="citi-table">
                            <thead>
                                <tr>
                                    <th style="width:30px;"></th>
                                    <th style="width:30px;"></th>
                                    <th style="width:30px;"></th>
                                    <th>Right Description</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr class="selected">
                                    <td><input type="checkbox" class="citi-checkbox" checked disabled /></td>
                                    <td><button class="btn-icon danger" title="Remove"><i class="fas fa-minus-circle"></i></button></td>
                                    <td>
                                        <button class="btn-icon primary" title="Expand"><i class="fas fa-chevron-down"></i></button>
                                    </td>
                                    <td><strong class="fw-600">View Accounts</strong></td>
                                </tr>
                                <tr>
                                    <td colspan="4" style="padding:0 12px 10px 12px;">
                                        <div class="right-detail-box">
                                            <div class="row">
                                                <label><input type="checkbox" checked /> Access</label>
                                                <label><input type="checkbox" checked /> Read</label>
                                                <label><input type="checkbox" /> Write</label>
                                                <label><input type="checkbox" /> Delete</label>
                                            </div>
                                        </div>
                                    </td>
                                </tr>
                                <tr>
                                    <td><input type="checkbox" class="citi-checkbox" checked disabled /></td>
                                    <td><button class="btn-icon danger" title="Remove"><i class="fas fa-minus-circle"></i></button></td>
                                    <td><button class="btn-icon" title="Expand"><i class="fas fa-chevron-right"></i></button></td>
                                    <td>Edit Transactions</td>
                                </tr>
                                <tr>
                                    <td><input type="checkbox" class="citi-checkbox" disabled /></td>
                                    <td><button class="btn-icon success" title="Assign"><i class="fas fa-plus-circle"></i></button></td>
                                    <td><button class="btn-icon" disabled style="opacity:0.2;"><i class="fas fa-circle"></i></button></td>
                                    <td>Approve Payments</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    <div class="pagination-bar">
                        <span class="info">1–3 of 5</span>
                        <div class="controls">
                            <button disabled><i class="fas fa-chevron-left"></i></button>
                            <button class="active">1</button>
                            <button>2</button>
                            <button><i class="fas fa-chevron-right"></i></button>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- ===== CHECKLIST ===== -->
        <div class="checklist-wrap">
            <div class="cl-header">
                <span class="icon"><i class="fas fa-check-double"></i></span>
                <h6>Audit Checklist</h6>
                <span class="count-badge">4 actions</span>
            </div>
            <div class="cl-body">
                <div class="cl-item">
                    <span class="dot"></span>
                    <span class="action">Assign Login</span>
                    <span class="desc">User <strong>jsmith</strong> → App <strong>Core Banking</strong></span>
                    <span class="time">just now</span>
                </div>
                <div class="cl-item">
                    <span class="dot" style="background:#16a34a;"></span>
                    <span class="action">Remove Dept</span>
                    <span class="desc">User <strong>mjohnson</strong> ← Dept <strong>IT</strong></span>
                    <span class="time">2 min ago</span>
                </div>
                <div class="cl-item">
                    <span class="dot" style="background:#d97706;"></span>
                    <span class="action">Suspend Login</span>
                    <span class="desc">User <strong>bwilliams</strong> → App <strong>Trade Portal</strong></span>
                    <span class="time">5 min ago</span>
                </div>
                <div class="cl-item">
                    <span class="dot" style="background:#dc2626;"></span>
                    <span class="action">Remove Right</span>
                    <span class="desc">User <strong>jsmith</strong> ← Right <strong>Approve Payments</strong></span>
                    <span class="time">12 min ago</span>
                </div>
            </div>
        </div>

        <!-- ===== ADD USER MODAL ===== -->
        <div class="modal-overlay" id="addUserModal" style="display:none;" onclick="if(event.target===this)this.style.display='none'">
            <div class="modal-box">
                <h5><i class="fas fa-user-plus"></i> Add New User</h5>
                <div class="field">
                    <label>User ID</label>
                    <input class="citi-input" placeholder="e.g. jsmith" />
                </div>
                <div class="field">
                    <label>First Name</label>
                    <input class="citi-input" placeholder="John" />
                </div>
                <div class="field">
                    <label>Last Name</label>
                    <input class="citi-input" placeholder="Smith" />
                </div>
                <div class="field">
                    <label>Default Department</label>
                    <select class="citi-select">
                        <option value="">— Select —</option>
                        <option>Engineering</option>
                        <option>Finance</option>
                        <option>IT</option>
                        <option>HR</option>
                    </select>
                </div>
                <div class="actions">
                    <button class="btn-sm outline" onclick="document.getElementById('addUserModal').style.display='none'">Cancel</button>
                    <button class="btn-sm primary" onclick="alert('User added!');document.getElementById('addUserModal').style.display='none'">
                        <i class="fas fa-plus"></i> Add User
                    </button>
                </div>
            </div>
        </div>

    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            document.addEventListener('keydown', function(e) {
                if (e.key === 'Escape') {
                    document.getElementById('addUserModal').style.display = 'none';
                }
            });
        });
    </script>

</body>
</html>
