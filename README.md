# MedPimped Supabase Configuration

This repository contains the Supabase database configuration for the MedPimped application.

## Database Schema

### Users Table
- `id` (uuid, primary key): References auth.users
- `email` (text, unique): User's email address
- `display_name` (text): User's display name
- `created_at` (timestamptz): Record creation timestamp
- `updated_at` (timestamptz): Record update timestamp

### Features
- Automatic user profile creation on signup
- Row Level Security (RLS) policies
- Users can only view and update their own data

## How it works
When a new user signs up through Supabase Auth:
1. A trigger `on_auth_user_created` is fired
2. The `handle_new_user()` function creates a corresponding record in the `users` table
3. The user's email is used as the default display name if none is provided

## Development

### Running Migrations
To apply these migrations to your Supabase project:

1. Install Supabase CLI
2. Link your project:
```bash
supabase link --project-ref ikyglcvucyuwdaxlsckq
```
3. Apply migrations:
```bash
supabase db push
```