# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

### Running the Application
- `composer dev` - Start all development services (server, queue, logs, and Vite) concurrently
- `php artisan serve` - Start Laravel development server only
- `npm run dev` - Start Vite for asset building
- `npm run build` - Build production assets

### Testing
- `composer test` - Run all tests (clears config and runs PHPUnit via artisan)
- `php artisan test` - Run tests directly
- Tests use Pest framework with PHPUnit as the base

### Code Quality
- `php artisan pint` - Format code (Laravel Pint for PSR-12 formatting)

### Database
- `php artisan migrate` - Run database migrations
- Database uses SQLite (database/database.sqlite)

## Architecture

This is a Laravel 12 application using the Livewire Starter Kit with the following key technologies:

### Frontend Stack
- **Livewire Volt** - Single-file Livewire components in Blade templates
- **Flux UI** - Livewire component library for UI elements
- **Tailwind CSS 4.0** - Utility-first CSS framework with Vite integration
- **Vite** - Asset bundling and hot module replacement

### Backend Stack
- **Laravel 12** with PHP 8.2+
- **SQLite** database for development
- **Livewire** for reactive components
- **Pest** testing framework

### Key Architectural Patterns

#### Livewire Volt Components
- Volt components are located in `resources/views/livewire/` 
- Settings pages use Volt routing: `Volt::route('settings/profile', 'settings.profile')`
- Volt mounts from both `resources/views/livewire/` and `resources/views/pages/`

#### Authentication
- Uses Laravel's built-in authentication with Livewire components
- Auth components in `resources/views/livewire/auth/`
- Routes defined in `routes/auth.php`

#### UI Structure
- Flux components for consistent UI (`resources/views/flux/`)
- Layout components in `resources/views/components/layouts/`
- Settings use a shared layout (`components/settings/layout.blade.php`)

#### Testing Structure
- Feature tests for authentication flows and main functionality
- Uses Pest with Laravel's TestCase base class
- RefreshDatabase trait available but commented out in Pest.php