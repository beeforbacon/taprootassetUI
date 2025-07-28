# Taproot Assets Interface

EXPECT BUGS!!!!!!! NOT PRODUCTION READY.

A comprehensive web-based terminal interface for managing Lightning Network nodes through Taproot Assets Protocol (TAP) and Lightning Terminal (LIT) CLI commands. Features multi-node connection management, command execution, and secure data handling with enterprise-grade encryption.

![Lightning Terminal Interface](https://img.shields.io/badge/Lightning-Network-orange) ![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?logo=typescript&logoColor=white) ![React](https://img.shields.io/badge/React-20232A?logo=react&logoColor=61DAFB) ![Node.js](https://img.shields.io/badge/Node.js-43853D?logo=node.js&logoColor=white)

<img width="844" height="419" alt="image" src="https://github.com/user-attachments/assets/bbe4e678-5cb4-49aa-b9d9-76326d084921" />


## 🚀 Features

### Multi-Node Management
- **Connection Management**: Create, activate, and manage multiple Lightning Network node connections
- **Secure Storage**: AES-256 encryption for all sensitive data (macaroons, TLS certificates)
- **Network Support**: Compatible with mainnet, testnet, and signet networks
- **CA Certificate Support**: Handle both self-signed and CA-signed certificates

### Command Interface
- **CLI Support**: Execute `litcli`, `tapcli`, and `lncli` commands
- **Terminal-like Interface**: Familiar command-line experience in the browser
- **Command History**: Persistent storage and retrieval of command execution history
- **Response Formatting**: JSON formatting, raw response view, and export capabilities

### Security & Performance
- **Enterprise Encryption**: AES-256 encryption for all sensitive connection data
- **PostgreSQL Database**: Persistent storage with automatic cleanup (7-day retention)
- **Rate Limiting**: Protection against abuse with configurable limits
- **Optimized Codebase**: Streamlined architecture with minimal dependencies

## 🛠️ Technology Stack

### Frontend
- **React** with TypeScript for type-safe development
- **Tailwind CSS** with shadcn/ui components for modern design
- **TanStack Query** for efficient server state management
- **Wouter** for lightweight client-side routing
- **Vite** for fast development and optimized builds

### Backend
- **Node.js** with Express.js framework
- **TypeScript** with ES modules for modern development
- **Drizzle ORM** with PostgreSQL for database operations
- **Helmet.js** for security headers and protection

### Database
- **PostgreSQL** with Neon Database serverless integration
- **Drizzle Kit** for schema management and migrations
- **Automated cleanup** for command history older than 7 days

## 🔧 Installation & Setup

### Prerequisites
- Node.js 18+ and npm
- PostgreSQL database (or Neon Database account)
- Lightning Network node with REST API access

### Environment Variables
```bash
DATABASE_URL=postgresql://username:password@host:port/database
NODE_ENV=development
```

### Installation
```bash
# Clone the repository
git clone https://github.com/beefalorian/taprootassetdashboard.git
cd taprootassetdashboard

# Install dependencies
npm install

# Set up database schema
npm run db:push

# Start development server
npm run dev
```

### Production Build
```bash
# Build for production
npm run build

# Start production server
npm start
```

## 📋 Usage

### Adding Lightning Network Connections

1. **Navigate to Connections**: Click the "Connections" tab in the sidebar
2. **Add New Connection**: Click "Add Connection" and provide:
   - Connection name (e.g., "mainnet-node-1")
   - Endpoint URL (e.g., "https://node.example.com:8080")
   - Network type (mainnet/testnet/signet)
   - Macaroon file (upload .macaroon file)
   - TLS Certificate (optional for CA-signed certificates)
  
   - <img width="197" height="383" alt="image" src="https://github.com/user-attachments/assets/2850a47d-2739-4ebc-9089-f5af1a28aac7" />


3. **Test Connection**: Verify connectivity before saving
4. **Activate Connection**: Select the connection for command execution

### Executing Commands

1. **Select CLI**: Choose between `litcli`, `tapcli`, or `lncli`
2. **Enter Command**: Type your command (e.g., `getinfo`, `listchannels`)
3. **Execute**: Click "Execute" or press Ctrl+Enter
4. **View Results**: See formatted JSON responses with execution time

### Example Commands

```bash
# Lightning Network commands
lncli getinfo
lncli listchannels
lncli newaddress

# Taproot Assets commands
tapcli assets list
tapcli assets mint --type normal --name "MyAsset" --supply 1000
tapcli addrs new --asset_id <asset_id> --amt 100

# Lightning Terminal commands
litcli accounts list
litcli sessions add --label "trading-session"
litcli orders submit --buy --amt 1000000
```

## 🔐 Security Features

### Data Protection
- **AES-256 Encryption**: All macaroons and TLS certificates encrypted at rest
- **Secure Headers**: Helmet.js protection against common vulnerabilities
- **Rate Limiting**: Configurable limits to prevent abuse
- **Input Validation**: Zod schema validation for all API endpoints

### Authentication
- **Macaroon-based Auth**: Standard Lightning Network authentication
- **TLS Support**: Full certificate validation for secure connections
- **Session Management**: PostgreSQL-backed session storage

## 📚 API Endpoints

### Connections
- `GET /api/connections` - List all connections
- `POST /api/connections` - Create new connection
- `PUT /api/connections/:id` - Update connection
- `DELETE /api/connections/:id` - Delete connection
- `PUT /api/connections/:id/activate` - Activate connection
- `POST /api/connections/test` - Test connection

### Command Execution
- `POST /api/execute/:cli` - Execute CLI command (litcli/tapcli/lncli)

### History
- `GET /api/history` - Get command history
- `DELETE /api/history` - Clear command history

## 🏗️ Architecture

### Project Structure
```
├── client/                 # React frontend
│   ├── src/
│   │   ├── components/    # UI components
│   │   ├── pages/         # Application pages
│   │   ├── hooks/         # Custom React hooks
│   │   └── lib/           # Utilities and API client
├── server/                # Express.js backend
│   ├── routes.ts          # API route definitions
│   ├── storage.ts         # Database operations
│   ├── security.ts        # Encryption and security
│   └── db.ts              # Database connection
├── shared/                # Shared types and schemas
└── [config files]         # TypeScript, Tailwind, Vite configs
```

### Database Schema
- **connections**: Store Lightning Network connection details
- **command_history**: Track command execution and responses

## 🚀 Deployment

### Development
```bash
npm run dev
```
Starts both frontend (Vite) and backend (Express) with hot reload.

### Production
```bash
npm run build
npm start
```
Creates optimized builds and runs production server.

### Environment Support
- **Development**: Hot reload, debug logging, error overlays
- **Production**: Optimized bundles, security headers, rate limiting

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔗 Links

- **Lightning Network**: https://lightning.network/
- **Taproot Assets**: https://github.com/lightninglabs/taproot-assets
- **Lightning Terminal**: https://github.com/lightninglabs/lightning-terminal
- **Lightning Labs**: https://lightning.engineering/

## ⚠️ Disclaimer

This software is for educational and development purposes. Always test thoroughly before using with mainnet funds. The authors are not responsible for any loss of funds.

---

**Built with ⚡ by Lightning Network enthusiasts**
